# 计划：在 a1.py 中增加冒泡排序例子

## 当前状态

[a1.py](file:///workspace/a1.py) 当前内容：

```python
import os
print("hello world")
print(os.getcwd())
```

## 实施步骤

### 步骤 1：在 a1.py 末尾添加冒泡排序函数

在现有代码之后，添加一个 `bubble_sort` 函数，包含：

- 函数定义：`def bubble_sort(arr):`
- 冒泡排序核心逻辑：双重循环，相邻元素比较与交换，优化提前退出
- 函数文档字符串说明

### 步骤 2：添加测试/演示代码

在函数定义之后，添加演示代码：

- 创建一个无序列表
- 调用 `bubble_sort` 函数进行排序
- 打印排序前和排序后的结果

### 预期最终代码结构

```python
import os
print("hello world")
print(os.getcwd())

def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break
    return arr

if __name__ == "__main__":
    sample = [64, 34, 25, 12, 22, 11, 90]
    print("排序前:", sample)
    sorted_arr = bubble_sort(sample)
    print("排序后:", sorted_arr)
```

## 影响范围

- 仅修改 `/workspace/a1.py` 一个文件
- 不影响现有功能（原有的 `print("hello world")` 和 `print(os.getcwd())` 保持不变）
