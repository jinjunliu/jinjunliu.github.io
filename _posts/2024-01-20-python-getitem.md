---
title: "Python __getitem__函数用例"
date: 2024-01-20
permalink: /posts/2024-01-20-python-getitem/
collection: posts
draft: true
tags:
  - Python
  - __getitem__
---

本文介绍如何使用Python读取NetCDF文件，以及如何将读取的NetCDF文件转换为PyTorch的Dataset格式。

# 构造Dataset类

```python
import os
import torch
import numpy as np
from torch.utils.data import Dataset, DataLoader
import xarray as xr

class NetCDFDataset(Dataset):
    def __init__(self, root_dir, transform=None):
        self.root_dir = root_dir
        self.transform = transform
        self.files = os.listdir(root_dir)

    def __len__(self):
        return len(self.files)

    def __getitem__(self, idx):
        if torch.is_tensor(idx):
            idx = idx.tolist()

        file_name = os.path.join(self.root_dir, self.files[idx])
        data = Dataset(file_name)
        data = data.variables['data'][:]
        data = np.transpose(data, (2, 0, 1))
        data = torch.from_numpy(data)
        data = data.float()

        if self.transform:
            data = self.transform(data)

        return data
```

# 构造DataLoader

```python
import torch
dataset = NetCDFDataset(root_dir='data')
dataloader = DataLoader(dataset, batch_size=1, shuffle=True)
```

# 读取数据

```python
for i, data in enumerate(dataloader):
    print(data.shape)
```

