---
title: 最大公约数
layout: post
author: Yi

---

理论：
  辗转相除法--一种求两个数最大公约数(greatest common divisor)的方法，
  理论基于【gcd(a,b)=gcd(b,a%b)】证明如下：

        假设c=gcd(a,b)且a/b=k......r【a=kb+r】
        令a=mc,b=nc则有 【a=mc=kb+r】->
                        【r=mc-kb】->
                        【r=mc-nkc】->
                        【r=(m-nk)c】所以c也是r的一个因子

        所以c也是b和r的公约数【b=nc】【r=(a-nk)c】
        但要证明c为最大公约数，必证n与a-nk 互质：证明如下

        【反证法】：
                 假设n=ey,m-nk=dy(y>1),
              	 a=mc=(dy+nk)c=(dy+eyk)c=cdy+ceky=(d+ek)cy
              	 b=nc=ecy
              	 则有cy>c 与gcd(a,b)=c 矛盾，所以可知n,m-nk 互质。
              	 继而gcd(a,b)=gcd(b,a%b)

理论：gcd(a,b)=gcd(b,a%b)

思想：都是判断b是否为零，是则输出a；否则递归调用或循环直至b为零时输出a;

C++三种实现：

        #include<iostream>
        using namespace std;

        int gcdt(int a,int b){//最爱最简洁，递归
        return b==0?a:gcdt(b,a%b);
        }

        int gcd(int a,int b){//循环
        int temp=b;
         while(temp){
              temp=a%b;
              a=b;
              b=temp;
         }
         return a;
        }

        int gcds(int a,int b){//递归
        if(!b){return a;}
        else {return gcds(b,a%b);}
        }

        int lcm(int a,int b){//最小公倍数（lowest common multiple):思想：两数相乘除以最大公约数。
         return a*b/gcdt(a,b);
        }
        int main(){
        cout<<gcd(9,3)<<endl;
        cout<<gcds(3,9)<<endl;
        cout<<gcdt(9,3)<<endl;
        cout<<lcm(9,3)<<endl;
        return 0;
        }

        例子2：
        //求1到n的最小公倍数

        #include<iostream>
        using namespace std;
        //最大公约数
        int gcd(int a,int b){
        return b==0?a:gcd(b,a%b);
        }
        //最小公倍数
        int lcm(int a,int b){
        return a*b/gcd(a,b);
        }
        //1到n的最小公倍数
        int nlcm(int n){
        if(n==1){return 1;}
        return lcm(n,nlcm(n-1));
        }

        int main(){
        int n;
        cin>>n;
        cout<<nlcm(n)<<endl;
        return 0;
        }
