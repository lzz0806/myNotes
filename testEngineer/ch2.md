### 1.1求任意n个数的最大公因数

**示例1：**
>**输入：[12, 18]**
>
>**输出：6**
>
>**解释：12 和 18 的公因子是 1、2、3、6**

```python
# 求一个数的所有因数
def common_factor(n) -> list:
    if n == 0:
        raise ValueError('0没有因数')
    cf = []
    for i in range(1, n + 1):
        if n % i == 0:
            cf.append(i)
    return cf
# 获取最大公因数
def highest_common_factor(val_list):
    tmp = []
    for val in val_list:
        # 将输入的所有数加入一个列表中
        factor_list = common_factor(val)
        tmp.extend(factor_list)
    count_dict = dict()
    for i in tmp:
        # 统计列表中每个数的出现频率
        if i not in count_dict.keys():
            count_dict[i] = 1
        else:
            count_dict[i] += 1
    val_count, key_count= 0, 0
    max_common_factor = 1
    for key, val in count_dict.items():
        # 遍历字典，统计出现频率最高的数为最大公约数，
        # 如果多个数出现频率相同取最大的
        if val >= val_count:
            val_count = val
            if key > key_count:
                max_common_factor = key
                key_count = key
    return max_common_factor
```