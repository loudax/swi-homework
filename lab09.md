# 洗衣机算法设计

## 自顶向下,逐步求精

自顶向下,逐步求精的方法。“自顶向下”是将复杂的问题划分为简单的问题，然后再描述简单的问题。而“逐步求精”的具体内涵是是将现实世界的问题经抽象转化为逻辑空间或求解空间的问题。复杂问题经抽象化处理变为相对比较简单的问题。经若干步抽象（精化）处理，最后到求解域中只是比较简单的编程问题。

## 应用：洗衣机算法设计

注水：

water_in_switch(open)

while(water_volume<h)

get_water_volume()

water_in_switch(close)

浸泡：

while(time<a)

time_counter()

漂洗:

water_in_switch(open)

while(water_volume<h)

get_water_volume()

water_in_switch(close)

while(time<b)

motor_run(left)

motor_run(right)

time_counter()

motor_run(stop)

water_out_switch(open)

while(water_volume>0)

get_water_volume()

water_out_switch(close)

脱水：

water_out_switch(open)

while(time<c)

motor_run(left)

motor_run(right)

time_counter()

motor_run(stop)

water_out_switch(close)

halt(success)
