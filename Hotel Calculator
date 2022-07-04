'''
给定两个数组（A1,A2，A3...）以及（B1，B2，B3..），枚举计算他们的加权平均数并打印
'''
import itertools
import numpy as np


# 计算酒店排名主函数
def Hotel_calculator(Hotel_prices, Hotel_rooms, target):
    Revenue = []

    # 列出所有可能价格排列，并转换为list
    List_hotel_prices = [int(Hotel_prices[i]) for i in range(len(Hotel_prices))]
    List_prices = list(itertools.permutations(List_hotel_prices))

    # 房间信息
    List_hotel_rooms = [int(Hotel_rooms[i]) for i in range(len(Hotel_rooms))]
    hotel_rooms_sum = sum(List_hotel_rooms)

    # 计算总的REVENUE
    for i in range(len(List_prices)):
        Single_Revenue = np.dot(List_prices[i], List_hotel_rooms)
        Single_Revenue = round(Single_Revenue/hotel_rooms_sum, 2)
        Single_Revenue_dif = round(abs(Single_Revenue - target), 2)
        list_i = list(List_prices[i])
        list_i.append(Single_Revenue)
        list_i.append(Single_Revenue_dif)
        Revenue.append(list_i)
        Revenue.sort(key=lambda takelast: takelast[-1])
    return Revenue


# 打印最接近的酒店排名计算结果
def print_closest_Result(Revenue):
    print('最接近target的数值是%d' % Revenue[0][-2])
    print('其RevPar排列顺序为：')
    print(Revenue[0][:-2])


# 打印所有酒店排名计算结果
def print_all_result(Revenue: list):
    print('全部计算结果如下(最后两位分别为计算结果以及同target的误差)：', end='\n')
    for i in range(len(Revenue)):
        print(Revenue[i], end='\n')


# 酒店排名计算运行函数
def calculation_main():
    Hotel_prices = input('pls input hotel RevPar: ').split(',')
    Hotel_rooms = input('pls input hotel rooms: ').split(',')
    target = int(input('pls input your target number(Must be an integer): '))

    Result = Hotel_calculator(Hotel_prices, Hotel_rooms, target)
    print_closest_Result(Result)

    test_call = input('Input y to show all results:\n')

    if test_call == 'y':
        print('酒店房间排序：', list(int(i) for i in Hotel_rooms))
        print_all_result(Result)


# 获取像素位置信息
def Get_pixel():
    Hotel_pixel = []
    Base_pixel = int(input('pls input the base pixel: \n'))
    Hotel_pixel.append(Base_pixel)
    Hilton_pixel = int(input('pls input your hotel pixel: \n'))
    Hotel_pixel.append(Hilton_pixel)
    Hotel_number = 1

    while True:
        Competitor_pixel = int(input('pls input the %d hotel pixel (input 0 to quit): \n' % Hotel_number))
        Hotel_pixel.append(Competitor_pixel)
        Hotel_number += 1

        if Competitor_pixel == 0:
            break

    return Hotel_pixel


# 通过像素计算竞争对手数字
def Pixel_calculator(Hotel_pixel: list):
    Hilton_real_number = int(input('pls input your hotel real OCC/ADR to start calculation: \n'))
    Hotel_pixel_result = [Hilton_real_number]
    for i in range(len(Hotel_pixel)-2):
        Competitor_number = (Hotel_pixel[i+2]-Hotel_pixel[0])/(Hotel_pixel[1]-Hotel_pixel[0])*Hilton_real_number
        Hotel_pixel_result.append(Competitor_number)
    return Hotel_pixel_result[:-1]  # 删除78行引入的最后一个无效信息0


# 输出像素计算结果
def print_pixel_result(Hotel_pixel_result: list):
    print('Pixel Simulation Result(First for Hilton)：\n')
    print(Hotel_pixel_result)


def Pixel_calcultion_func():
    print_pixel_result(Pixel_calculator(Get_pixel()))


if __name__ == '__main__':
    while True:
        try:
            task = input('Input 1 for RevPar calculation, input 2 for Pixel simulation.\nTo quit input exit：\n')

            if task == '1':
                calculation_main()
            elif task == '2':
                Pixel_calcultion_func()
            elif task == 'exit':
                break
            else:
                print('Invalid input, pls try again! \n')

            print('='*30)

        except ValueError:
            print('Invalid input, pls try again! \n')
