---
date: 2017-04-24 16:54:56+00:00
layout: post
title: Bash数组
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [数组声明方式１](#step1)
2. [数组声明方式２](#step2)
3. [获取所有数组内容](#step3)
4. [获取指定下标内容](#step4)
5. [获取数组长度](#step5)

---
#### <span id="step1">数组声明方式１</span>
> 数组声明方式１：arrayname=(值１，值２，...，值ｎ)
```
#!/bin/bash
name=("张三" "李四" "王五")
```

#### <span id="step2">数组声明方式２</span>
> 数组声明方式２：arrayname[index]=值
```
#!/bin/bash
#需要注意的是数组下标从０开始
name[0]="张三"
name[1]="李四"
name[2]="王五"
```

#### <span id="step3">获取所有数组内容</span>
> 获取所有数组内容：${arrayname[*]}或${arrayname[@]}
```
#!/bin/bash
name=("张三" "李四" "王五")
echo "所有同学的名字${arrayname[*]}"
echo "另外一种方式${arrayname[@]}"
```

#### <span id="step4">获取指定下标内容</span>
> 获取指定小标内容：${arrayname[index]}
```
#!/bin/bash
name=("张三" "李四" "王五")
echo "获取第一个同学的名字：${arrayname[0]}"
echo "获取第二个同学的名字：${arrayname[1]}"
echo "获取第三个同学的名字：${arrayname[2]}"
```

#### <span id="step5">获取数组长度</span>
> 获取数组长度：${#arrayname[*]}或${#arrayname[@]}
```
#!/bin/bash
name=("张三" "李四" "王五")
echo "数组长度获取方式１：${#arrayname[*]}"
echo "数组长度获取方式２：${#arrayname[@]}"
```
