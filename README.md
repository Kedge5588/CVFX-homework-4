# CVFX-homework-4
# HW4 Report
## Sequence of moving-forward images in NTHU
![](https://i.imgur.com/gYK0hRD.jpg)
我們選擇在台達的走廊拍攝，每走一步路拍一張，上圖是連續16張的結果。
## Feature extraction and matching results

以下圖片為使用ORB作Feature extraction，然後跟下一步做matching得到的結果。

![](https://i.imgur.com/UJyHlkW.jpg)

![](https://i.imgur.com/lQKpDgP.jpg)

![](https://i.imgur.com/DIEDkO1.jpg)

![](https://i.imgur.com/AYsms18.jpg)

從上圖可以得知，整體matching的效果還不錯，很多特徵點也有被找出來，像是門緣或是牆上的公告。
 

## Infinite zooming effect
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/hUmGMsKa6cI/0.jpg)](https://www.youtube.com/watch?v=hUmGMsKa6cI)

## Implement different feature extrators
我們在兩張相差一步之間距離的相片比較其特徵，以下利用不同的演算法做feature extraction。

* ORB

![](https://i.imgur.com/3IFIjOC.jpg)

ORB主要是machine learning的應用，找出特徵點附近16個像素中，找出最符合特徵點的點。
從上圖可以發現，左圖的點都有成功對應到下一步(右圖)，且也有找到很多重要的特徵，像是門框、牆上的公告，都是可以作為stiching的重要資訊。

* SIFT

![](https://i.imgur.com/tEuzDyW.jpg)

SIFT主要是經由高斯函數的計算，算出有可能的對應圖像空間，找出相對應的特徵點，再經分析，去除可能性較低的特徵點，得到最終結果。
由上圖可以發現SIFT找出的特徵點非常多，但可以發現圖片右側地板的特徵點，對應到的位置非原圖(左圖)的位置，其餘的特徵點，與實際位置還是有一定的距離差。

* SURF

![](https://i.imgur.com/F7cnTQq.jpg)


SURF主要是優化SIFT的運算方法，減少繁瑣的運算。
由上圖可以發現，SURF相較於SIFT找出較少的特徵點，但也減少了像是SIFT方法中，出現非對應特徵點的情況，再者，就SURF找出的特徵點，相較於ORB找出的特徵點，特徵點的品質較低，並非整張圖片較為明顯的特徵。

------------------------------------------------

* ORB、SIFT、SURF比較


|              | ORB      | SIFT     |SURF   |
| --------     | -------- | -------- |-------|
|計算速度       | 快        | 慢        |中     |
|找出特徵點的數量 |中        |多         |中     |
|特徵點品質      |高        |低         |中     |

從上表可以得知，SIFT雖然計算速度較慢，但對特徵點的找尋有一定的成效，對於較細緻的stiching，SIFT方法有其優勢。SURF方法，在計算速度上進步了不少，也改進了很多SIFT在找特徵點上的缺點。ORB在各方面都勝於其他兩種方法，也找出圖片中較為明顯的特徵點。

## Enhance Effect
