# ...................................

以下為重現實驗教學

## 下載程式碼
```
git clone https://github.com/CodeBaron7/
```

## 資料準備

1. 至官方Download Dataset下載Private Testing Dataset_v2.zip
2. 下載已訓練完成的模型 : 
3. 下載調整後的訓練資料集 : 
      訓練資料調整
      1. img0040.png 與 img0040.txt刪除，
      2. img0201 ~ img0400 當作驗證集

準備好後將資料照著下方檔案結構，擺放資料，請注意檔名與路徑需一致。
### 檔案結構:
```
.
└── TEAM_2096_UAV
      ├─code
      |   ├─       # Private Testing Dataset_v2
      |   ├─       # 
      |   ├─       #
      |   ├─       #
      |   ├─       #
      |   ├─       #
      |   └─ 
      ├─LICENSE
      ├─README.md         
      └─requirements.txt
```
注意: Dataset 與result 內各資料夾僅有一層，例如Dataset\Submit_Image打開即為Private_00000000.jpg ~ Private_00000183.jpg

## 環境配置:

   以下2種方式可2擇1選用:

### 1.於Local端執行
   下方有環境建置教學
   
   作業系統 : Win10 or Linux
   
   Python : 3.9.9         (建議至少3.8以上)
   
   Pytorch : 1.11.0+cu113 (根據CUDA Version選擇)
   
   ***訓練時GPU Memory至少需24GB
   
   CUDA Version: 11.5

### Local端虛擬環境建置教學
   建立虛擬環境並進入
```
Python -m venv yolov7_venv
cd yolov7_venv\Scripts
activate
```
   更新pip與setuptools
```sh
python -m pip install --upgrade pip
pip install --upgrade setuptools
```
   依cuda版本安裝對應pytorch函式庫
```sh
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu113
```
   至requirements.txt目錄下安裝其餘函式庫
```sh
pip install -r requirements.txt
```

### 2.執行於TWCC CCS cm.super
      
   容器映像檔pytorch-22.05-py3
  
   至requirements.txt目錄下安裝其餘函式庫
```sh
pip install -r requirements.txt
```

## Train
   至TEAM_2096_UAV\code路徑下輸入  
```sh
python train_aux.py --adam
```
   訓練後模型存放於runs\train\v18\weights

## Inference
   至TEAM_2096_UAV\yolov7路徑下執行
```sh
python detect.py --save-txt
```
Inference後產生的submission.csv提交檔存放於TEAM_2096_UAV\code目錄下


