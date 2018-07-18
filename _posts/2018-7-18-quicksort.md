---
title: 快速排序
author: Yi
layout: post
icon: fa-lightbulb-o
---
快速排序：
           采用分治法思想，选取一值作为轴元素，把小于等于它的换到它的左边，大于它的换到它的右边，所以轴元素就得到了排序的最终位置。
            然后再对轴元素两边的数分别递归采用如上的【分割策略】。

    【分割策略】具体实现思想有以下两种：

            a.
			    对于需要排序的数组：
				                 在（left<right）下【循环】以下操作：
										 先用一个临时变量存储第一个值作为轴元素（当然也可取其他数）
										 以数组下标作为left指针，从数组第一个元素开始
										 以数组的下标作为right指针从数组最一个元素后开始向前扫描，
                                         取到第一个小于等于轴元素的值为止
										 把right指向的值赋给left
										 left指针向后扫描，取到第一个大于轴元素的值为止
										 把left指向的值赋给right
								 当（left=right)时：
								         把轴元素放到left的位置即可。

				接下来就如此分别地递归left的左右两边。(0~left-1,left+1~n)



			b.
			    对于需要排序的数组：
				                在（left<=right）下【循环】以下操作：
								         先用一个临时变量存储第一个值作为轴元素（当然也可取其他数）
								         left和right 指针双向扫描，left 取到第一个大于轴元素的值为止
                                          right 取到第一个小于等于轴元素的值为止
										 交换left 和right 指向的值，(left++,right--)
							    当（left>right)后：
								         把轴元素放到right的位置即可。

				接下来就如此分别地递归right的左右两边。(0~right-1,right+1~n)


------------------------------------分割线--------------------------------------------------------------------------------


 以下是两个分割策略不同的例子：

     a:
        #include<iostream>
        using namespace std;
        void quick(int A[],int start,int end)
        {
        if(start<end){
        int left=start,right=end;
        int temp=A[start];
        while(left<right){//一旦left==right,就说明执行结束了，需以left（right)为分线开始下一轮。
                while(left<right&&A[right]>temp)
                        right--;
                A[left]=A[right];
                while(left<right&&A[left]<=temp)//注意此处的等于符不能少啊，不然当出现相等时left++执行不了就死循环了。
                        left++;
                A[right]=A[left];
                }
                A[left]=temp;//此时left的位置就是轴元素的位置（实则right也完全可以）
                quick(A,start,left-1);
                quick(A,left+1,end);
        }
        }
        int main(){
        int B[]={3,45,56,79,79};
        quick(B,0,4);
        for(int i=0;i<5;i++){
                cout<<B[i]<<endl;
        }
        return 0;
        }

      b:
        #include<iostream>
        using namespace std;
        #define N 100
        //此处的交换函数其实C++自带的有，但我想强调交换的必须是指针（地址），否则交换的只是实参的副本，达不到效果。
        void swap(int *left,int *right){
        int temp;
        temp=*left;
        *left=*right;
        *right=temp;}
        void QuickSort(int data[],int start,int end)
        {
        int pivot=data[start];
        int left=start,right=end;
        while(left<=right){   //在以下执行的所有条件中都有等于一条件（方便记，其实有的地方不要也行）
                while(left<=right&&data[left]<=pivot){
                        left++;
                }
                while(left<=right&&data[right]>=pivot){
                        right--;
                }
                if(left<=right){
                        swap(&data[right],&data[left]);
                        left++;
                        right--;
                }
        }
        //此处必须是和right位置值交换，因为当left>right 后，right指向的值一定是小于轴元素的，
        //所以right指向的值符合交换到轴元素前边的条件。而left则不符合。
        swap(&data[start],&data[right]);
        QuickSort(data,start,right-1);
        QuickSort(data,right+1,end);
        }

        int main(){
        int A[]={6,64,62,26};
        QuickSort(A,0,3);
        for(int i=0;i<4;i++){
                cout<<A[i]<<endl;
        }
        }
