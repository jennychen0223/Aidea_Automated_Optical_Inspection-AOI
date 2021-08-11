# AOI瑕疵檢測
## 專案介紹

自動光學檢查（Automated Optical Inspection，簡稱 AOI），為高速高精度光學影像檢測系統，運用機器視覺做為檢測標準技術，可改良傳統上以人力使用光學儀器進行檢測的缺點，應用層面包括從高科技產業之研發、製造品管，以至國防、民生、醫療、環保、電力…等領域。由工研院電光所提供的 AOI 影像資料，來判讀瑕疵的分類，藉以提升透過數據科學來加強 AOI 判讀之效能。

## 資料來源

本次資料是利用Aidea平台釋出作為開放性議題，提供參賽者建立分類模型進行預測。

資料來源：https://aidea-web.tw/topic/285ef3be-44eb-43dd-85cc-f0388bf85ea4

## 專案步驟：

- 了解資料
- 資料處理
- 模型評估
- 模型簡介
- 未來探討

## 了解資料

1. 訓練資料：2,528張
3. 測試資料：10,142張
4. Label：6個類別(正常類別 + 5種瑕疵類別)
5. 影像尺寸：512x512

<img width="387" alt="截圖 2021-08-11 上午9 40" src="https://user-images.githubusercontent.com/81677812/129036800-9e3bfe0c-d796-4651-b75a-215e3f7abcf8.png">

## 資料處理

1. 拆分Train資料：將圖片依7 : 1.5 : 1.5的比例分配至Train、Test、Valid三個資料夾內，並且按照圖片的分類放置0、1、2、3、4、5的資料夾內
2. 生成資料：利用ImageDataGenerator方法，將圖片縮放、旋轉、翻轉等增強訓練資料

## 模型評估

|    模型結構    |  準確率 |
|---------------|--------| 
|  DenseNet121  | 98.29% |
|    ResNet50   | 94.60% |
|     VGG-16    | 91.61% | 


- DenseNet121訓練過程

<img width="403" alt="DenseNet121 _50_2" src="https://user-images.githubusercontent.com/81677812/129036705-8bb7f73e-49fa-4b80-b88f-b801f8449b5c.png">
<img width="397" alt="DenseNet121_50_1" src="https://user-images.githubusercontent.com/81677812/129036718-02b86f22-c3a2-4e38-8bbd-4193b6780fb9.png">

- VGG-16訓練過程

<img width="408" alt="VGG16_2" src="https://user-images.githubusercontent.com/81677812/129052117-88b3a0f9-e870-4aa6-b150-551d251790d3.png">
<img width="393" alt="VGG16_1" src="https://user-images.githubusercontent.com/81677812/129052132-a906c7cc-acfc-45fd-be7f-efdf49bd9ba6.png">

- ResNet50訓練過程

<img width="390" alt="image" src="https://user-images.githubusercontent.com/81677812/129052272-1d615caa-a943-4573-b051-d6ad394a00c7.png">
<img width="398" alt="image" src="https://user-images.githubusercontent.com/81677812/129052346-e81ed9ae-ebcd-41f8-9c2c-a4e54eeaaae7.png">

## 模型簡介
### DenseNet121
又稱密集卷積網絡(Dense Connection)，基本思路與ResNet一致，以前饋方式將每一層連接到其他每一層。而具有L層的傳統卷積網絡有L個連接——每層與其後續層之間有一個連接——而我們的網絡有L(L+1)/2 個直接連接。對於每一層，所有先前層的特徵圖用作輸入，其自身的特徵圖用作所有後續層的輸入，使DenseNet有在參數與計算成本更少的優點，比ResNe更優的性能

優點：
- 減輕了梯度消失的問題，使模型不容易過擬合
- 加強了特徵傳播，鼓勵特徵重用，大大減少了參數的數量，提高訓練效率
- 增強了特徵在各個層之間的流動,因為每一層都與初始輸入層還有最後的由loss function得到的梯度直接相連。

<img width="365" alt="image" src="https://user-images.githubusercontent.com/81677812/129048989-348266ed-8854-41f8-bcb4-99645c4418e9.png">

### ResNet50(Residual Neural Network)
又稱殘差神經網路，在2015年被提出，在ImageNet比賽classification任務上獲得第一名，因爲它“簡單與實用”並存。在適當的深度模型中添加更多層會導致更高的訓練錯誤，利用跳過某些層的快捷方式，使用額外的權重矩陣來學習跳躍權重，解決了“隨着網絡加深，準確率下降”的問題。
<img width="242" alt="image" src="https://user-images.githubusercontent.com/81677812/129045888-389307c7-4621-4431-97f9-dfda40179629.png">

### VGG-16(Visual Geometry Group)
VGG是由牛津大學計算機視覺組Visual Geometry Group提出(這也是VGG名稱的由來)。主要貢獻是使用更多的隱藏層，大量的圖片訓練，提高準確率至90%。VGG16/VGG19分別為16層(13個卷積層及3個全連接層)與19層(16個卷積層及3個全連接層)，結構為：
- 13層卷積層，一個數字為卷積核大小，第二個數字為卷積層通道數
- 3層全連接層
- 5層最大池化層(maxpool)
- 卷積層與全連接層具有權重係數，因此也被稱為權重層，總數目為13+3=16，這即是VGG16中16的來源。

優/缺點
- VGG的架構簡單統一
- 證明較深的層數能提高效能
- 參數量龐大，計算資源需求高
- 訓練時間過長，難以調整參數
<img width="678" alt="image" src="https://user-images.githubusercontent.com/81677812/128550735-84eab772-df2f-43ed-9b30-74b09877b486.png">

## 未來探討
後續想再試試其他CNN模型架構：LeNet、AlexNet、GoogleLeNet、探討其不同差異性。
<img width="900" alt="image" src="https://user-images.githubusercontent.com/81677812/128622597-2bebec61-cc6f-437e-9ce2-f1df81e855fb.png">

(圖片來源：http://p.migdal.pl/2017/04/30/teaching-deep-learning.html)
