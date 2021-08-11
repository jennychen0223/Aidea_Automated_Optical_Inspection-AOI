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
- 資料處理
- 模型評估

## 了解資料

1. 訓練資料：2,528張、2個欄位
3. 測試資料：10,142張、2個欄位
4. Label：瑕疵分類類別（0、1、2、3、4、5）

<img width="387" alt="截圖 2021-08-11 上午9 40" src="https://user-images.githubusercontent.com/81677812/129036800-9e3bfe0c-d796-4651-b75a-215e3f7abcf8.png">

## 資料處理

1. 拆分Train資料：將圖片依7 : 1.5 : 1.5的比例分配至Train、Test、Valid三個資料夾內，並且按照圖片的分類放置0、1、2、3、4、5的資料夾內
2. 生成資料：利用ImageDataGenerator方法，將圖片縮放、旋轉、平移等增強訓練資料

## 模型評估

|    模型結構    |  準確率 |
|---------------|--------| 
|  DenseNet121  | 98.29% |
|     VGG-16    | 91.61% | 96.87%
|    ResNet50   | % |

- DenseNet121訓練過程
<img width="403" alt="DenseNet121 _50_2" src="https://user-images.githubusercontent.com/81677812/129036705-8bb7f73e-49fa-4b80-b88f-b801f8449b5c.png">

<img width="397" alt="DenseNet121_50_1" src="https://user-images.githubusercontent.com/81677812/129036718-02b86f22-c3a2-4e38-8bbd-4193b6780fb9.png">

- VGG-16訓練過程



- ResNet50訓練過程


### DenseNet121簡介


### VGG-16簡介
VGG 是英國牛津大學 Visual Geometry Group 的縮寫，主要貢獻是使用更多的隱藏層，大量的圖片訓練，提高準確率至90%。VGG16/VGG19分別為16層(13個卷積層及3個全連接層)與19層(16個卷積層及3個全連接層)，結構為：
- 13層卷積層，一個數字為卷積核大小，第二個數字為卷積層通道數
- 3層全連接層
- 5層最大池化層(maxpool)
- 卷積層與全連接層具有權重係數，因此也被稱為權重層，總數目為13+3=16，這即是VGG16中16的來源。

<img width="678" alt="image" src="https://user-images.githubusercontent.com/81677812/128550735-84eab772-df2f-43ed-9b30-74b09877b486.png">
(圖片來源：https://www.researchgate.net/figure/The-flow-of-the-classification-and-visualization-in-the-VGG-16-DCNN-model-The-class-of-a_fig1_338770849)

### ResNet50簡介

### 繼續探討
後續想再試試其他CNN模型架構：VGG-19、LeNet、AlexNet、GoogleLeNet、探討其不同差異性。
<img width="900" alt="image" src="https://user-images.githubusercontent.com/81677812/128622597-2bebec61-cc6f-437e-9ce2-f1df81e855fb.png">

(圖片來源：http://p.migdal.pl/2017/04/30/teaching-deep-learning.html)
