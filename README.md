# AOI瑕疵檢測
## 專案介紹

自動光學檢查（Automated Optical Inspection，簡稱 AOI），為高速高精度光學影像檢測系統，運用機器視覺做為檢測標準技術，可改良傳統上以人力使用光學儀器進行檢測的缺點，應用層面包括從高科技產業之研發、製造品管，以至國防、民生、醫療、環保、電力…等領域。由工研院電光所提供的 AOI 影像資料，來判讀瑕疵的分類，藉以提升透過數據科學來加強 AOI 判讀之效能。

## 成果

<img width="1157" alt="image" src="https://user-images.githubusercontent.com/81677812/128591783-84b8cbc3-0b14-4589-a091-6c968a1e488e.png">

## 資料來源

本次資料是利用Aidea平台釋出作為開放性議題，提供參賽者建立分類模型進行預測。

資料來源：https://aidea-web.tw/topic/285ef3be-44eb-43dd-85cc-f0388bf85ea4

## 專案步驟：

- 了解資料
- 資料前處理
- 建立模型

## 了解資料

1. 訓練資料：2,528張、2個欄位
3. 測試資料：10,142張、2個欄位
4. Label：瑕疵分類類別（0、1、2、3、4、5）

## 資料前處理

1. 拆分Train資料：將圖片依7 : 1.5 : 1.5的比例分配至Train、Test、Valid三個資料夾內，並且按照圖片的分類放置0、1、2、3、4、5的資料夾內
2. 生成資料：爲增加圖片進行訓練，利用ImageDataGenerator方法，將圖片縮放、旋轉、平移等產生新的圖片


## 建立模型
本專案我利用VGG-16當base model訓練，準確率達90.9%，在Aidea其他參賽者有達到更好成績，之後想再嘗試其他CNN模型架構：LeNet、AlexNet、VGG、GoogleLeNet、ResNet。
### VGG-16簡介
VGG 是英國牛津大學 Visual Geometry Group 的縮寫，主要貢獻是使用更多的隱藏層，大量的圖片訓練，提高準確率至90%。VGG16/VGG19分別為16層(13個卷積層及3個全連接層)與19層(16個卷積層及3個全連接層)，結構為：
- 13層卷積層(convX-XXX)，第一個數字為卷積核大小，第二個數字為卷積層通道數
- 3層全連接層(FC-XXXX)
- 5層最大池化層(maxpool)
- 卷積層與全連接層具有權重係數，因此也被稱為權重層，總數目為13+3=16，這即是VGG16中16的來源。

<img width="678" alt="image" src="https://user-images.githubusercontent.com/81677812/128550735-84eab772-df2f-43ed-9b30-74b09877b486.png">
(圖片來源：https://www.researchgate.net/figure/The-flow-of-the-classification-and-visualization-in-the-VGG-16-DCNN-model-The-class-of-a_fig1_338770849)


