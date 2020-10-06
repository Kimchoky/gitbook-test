# 서버 현황

## CPU

### sar

시스템지표를 저장하고 확인한다.  
자세한 내용은 링크 참조  : [https://brunch.co.kr/@lars/9](https://brunch.co.kr/@lars/9)

```c
$ sar -f /var/log/sa/sa01  // 1일의 데이터
```

## Memory

### sar

```c
$ sar -r -f /var/log/sa/sa01  // 1일의 데이터
```

### free

메모리 사용현황을 보여준다.

```c
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            31G        2.3G         16G        947M         12G         27G
Swap:          9.8G          0B        9.8G
```

## Script

### CPU Activity

* 평균 사용률, 최대 사용률 \(최근 한 달\)

```c
#!/bin/bash
cd
sar -f /var/log/sa/sa01 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' > sar.out
sar -f /var/log/sa/sa02 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa03 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa04 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa05 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa06 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa07 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa08 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa09 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa10 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa11 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa12 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa13 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa14 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa15 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa16 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa17 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa18 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa19 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa20 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa21 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa22 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa23 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa24 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa25 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa26 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa27 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa28 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa29 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{if ($9!="") print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa30 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{if ($9!="") print 100-sum/cnt" "max}' >> sar.out
sar -f /var/log/sa/sa31 | awk '{sum+=($1=="Average:"?0:$9);cnt+=(sum==0||$9==""||$1=="Average:"?0:1);max=(cnt>0&&$9!=""&&max<(100-$9)?(100-$9):max);}END{if ($9!="") print 100-sum/cnt" "max}' >> sar.out
cat sar.out | awk '{sum+=$1;cnt+=1;max=(max<$2)?$2:max;}END{print "CPU Avr="sum/cnt" Max="max}'
```

### Memory Usage

* 평균 사용률, 최대사용률 \(최근 한 달\)
* 실질사용률\(%\) = $$(memused - buffers - cached) / (memfree + memused) * 100$$ 

```c
#!/bin/bash
cd
sar -r -f /var/log/sa/sa01 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}'  > sar.out
sar -r -f /var/log/sa/sa02 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa03 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa04 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa05 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa06 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa07 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa08 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa09 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa10 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa11 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa12 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa13 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa14 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa15 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa16 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa17 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa18 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa19 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa20 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa21 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa22 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa23 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa24 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa25 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa26 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa27 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa28 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa29 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{if (a==1) print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa30 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{if (a==1) print sum/cnt*100" "max*100}' >> sar.out
sar -r -f /var/log/sa/sa31 | awk '{a=($1=="Linux"||$1=="Average:"||$1==""||$3=="kbmemfree"?0:1);mu=(a==0?0:($4-$6-$7)/($3+$4));sum+=mu;cnt+=a;max=(a==1&&max<mu?mu:max);}END{if (a==1) print sum/cnt*100" "max*100}' >> sar.out
cat sar.out | awk '{sum+=$1;cnt+=1;max=(max<$2)?$2:max;}END{print "Mem Avr="sum/cnt" Max="max}'
```

