# AI靈丹軟體
本AI標注、訓練、辨識與管理軟體，是基於網路架構的邊緣運算私雲服務，彈性化的架構有利於未來擴充於於公雲SaaS端服務。邊緣運算私雲服務能確保使用者的資料集在企業內部，不會有資料外洩的疑慮，公雲服務亦可提供便捷的SaaS端服務。整體系統架構彈性兼顧未來擴充性。

又由於影像標記服務需要管理大量照片與標記資料集，一般而言、一個AI辨識物種需要日夜間各個角度照片3000張及標記，本軟體提供半自動標記服務增加標記效率，亦能夠批次上傳已經標記好的資料集。此外本系統已經系統化支援YOLOv5、YOLOv7、YOLOv8、YOLOv11、YOLOv11 segmeation 的指令集，無須具程式設計背景便可進行繁瑣的AI模型訓練，完成AI模型的辨識與推論，進而管理每一個經長時間訓練的模型。

## 📽️ 影像展示
相關辨識影像展示與操作教學，請參閱我們的官方頻道：
👉 [胡斯科技 Ailixir YouTube 頻道](https://www.youtube.com/@ailixirailixir)

![相關辨識影像展識](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo.jpg)

## 📞 購買與技術支援
如需購買軟體授權或技術支援，請聯繫：
* **Email**: [aailixir@gmail.com](mailto:aailixir@gmail.com)
* **聯絡我們**: [胡斯科技官方網站](https://anno.ailixir.com.tw/#contact)

# 第一章: 使用前準備
## 軟體安裝
請下載AI靈丹軟體安裝包，使用滑鼠雙敲執行安裝Ailixir AI靈丹軟體。

<img width="648" height="448" alt="image" src="https://github.com/user-attachments/assets/55c3708e-7c4b-460a-89bc-019e4777143f" />

## CUDA安裝
### Windows 系統安裝步驟
在 Windows 上安裝 CUDA 相對直觀，主要透過圖形化安裝精靈來完成。

1. 更新 NVIDIA 顯示卡驅動程式 
在安裝 CUDA 之前，請先前往 NVIDIA 官方網站下載並安裝適用於你顯示卡的最新版驅動程式。如果安裝舊版 CUDA，最新的驅動程式通常可以向下相容。

2. [下載 CUDA Toolkit] (https://developer.nvidia.com/cuda-downloads)
前往 NVIDIA CUDA Toolkit 官方下載頁面。
依序選擇你的作業系統條件：

* Operating System: Windows
* Architecture: x86_64
* Version: 10 或 11
* Installer Type: exe (local)

點擊下載安裝檔（檔案通常有幾 GB 大小）。

3. 執行安裝程式：雙擊下載的 .exe 檔案進行安裝。建議選擇 「精簡 (Express)」 安裝，這會自動為你安裝所有必要的組件並設定好 Windows 環境變數。如果你已有較新版的顯示卡驅動，安裝程式會提示覆蓋，通常保留較新版本的驅動即可。

4. 驗證安裝結果：安裝完成後，按下 Win + R，輸入 cmd 開啟命令提示字元，然後輸入以下指令：
   
```
nvidia-smi
```
![nvidia-smi](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_nvidia.jpg)

### Linux (Ubuntu) 系統安裝步驟
1. 在 Linux 系統中，通常建議使用終端機指令並透過 .deb 或 .run 檔案來安裝。1.安裝 NVIDIA 顯示卡驅動程式：需重新開機。開啟終端機，先更新系統套件庫，然後讓系統自動尋找並安裝最適合的 NVIDIA 驅動程式：

```
sudo apt update
sudo ubuntu-drivers autoinstall
sudo reboot
```

2. 下載與安裝 CUDA Toolkit：前往 NVIDIA 官方下載頁面，選擇 Linux -> x86_64 -> Ubuntu -> 你的版本 (如 22.04 或 24.04) -> deb (local)。網頁下方會自動生成對應的終端機指令（通常包含下載 .pin 檔、下載 .deb 檔、加入金鑰並透過 apt 安裝 cuda-toolkit）。請依序複製並在終端機中執行這些指令。

3. 設定環境變數：非常重要。安裝完成後，系統還不知道 CUDA 的路徑。你需要手動將它加入環境變數中。使用文字編輯器打開 ~/.bashrc 檔案，在最底端加入以下兩行（請將 cuda-12.x 替換為你安裝的實際版本號）：

```
export PATH=/usr/local/cuda-12.x/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-12.x/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
4. 驗證與檢查狀態：
輸入 nvcc --version 確認編譯器已正確安裝。接著，你可以使用 NVIDIA 系統管理介面來查看 GPU 的即時狀態與資源佔用。

## 訓練主機需求
* 作業系統：Windows 10、Windows 11 <BR>
* GPU需求：RTX20系列、RTX30系列、RTX40系列、RTX50系列 <BR>
* 記憶體RAM：4GB以上 <BR>

## Agentic AI 動態載入模型
系統支援以下模型的動態載入與訓練：

* YOLOv5 <BR>
* YOLOv7 <BR>
* YOLOv8 <BR>
* YOLOv11 <BR>
* YOLOv11-Seg (Segmentation) <BR>

# 第二章: 開始使用
安裝完畢並啟動服務後，請開啟瀏覽器並輸入以下網址進入系統：

http://127.0.0.1:8080 或
http://localhost:8080 

您可以輸入預設使用者名稱及密碼：

	使用者名稱：demo@example.com
	密碼：demo

輸入完使用者名稱及密碼後，請點選「登錄」鍵。


<img width="1920" height="963" alt="image" src="https://github.com/user-attachments/assets/8a00ce62-53ad-40f2-a202-8ed6dc68ef31" />

## 環境設定套件總覽
登入系統後，請先導覽至左側選單的 「AI 模型訓練」 並點選 「套件總覽」 按鈕。系統會自動偵測 CUDA 及相關必要套件（如 Git、PyTorch、PyYAML）是否安裝成功。

💡 提示：這個功能可免除使用者手動進行複雜環境設定的困擾。若顯示未安裝，可直接點選「套件診斷」進行動態安裝。

![相關辨識影像展識](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_install.jpg)

## 套件總覽
若一切安裝順利，點選「套件總覽」按鈕，會顯示相關必要元件如Git、PyTorch、PyYAML會顯示在套件總覽並顯示安裝狀態。

![套件總覽](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_pytorch.jpg)

## 套件診斷
若安裝不成功，可以點選「套件診斷」按鈕，進行安裝。

![套件診斷](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_step1.jpg)

# 第三章: AI資料集介紹
影像AI資料集是照片圖檔的集合，標注資料集(txt文字檔)則是教導AI的一個過程，如下圖所示為事先標記好的資料集。 

⚠️ 照片圖檔僅支援 jpg、jpeg、png、bmp格式

## AI資料集設定畫面

<img width="1906" height="954" alt="image" src="https://github.com/user-attachments/assets/f056a99b-c7d4-47fe-889f-a70e509bcf72" />

## AI資料集設定
請先點選左邊的導覽選單「AI資料集設定」進行「群組」及「資料集」設定，點選「新增群組」進行群組管理。


## 資料集群組新增
請輸入群組名稱來建立群組。

<img width="1920" height="479" alt="image" src="https://github.com/user-attachments/assets/840c638e-cf99-40a1-97f0-544963f23c1a" />

## 資料集新增
點選該新增群組可在該群組下點選「資料集新增」按鈕。新增完資料集後可以開始建立資料集。群組為相同的資料集，共享統樣的物件種類(names檔案)。
<BR>
<BR>
+ 資料集名稱: 可以用來記錄辨識用
+ 群組名稱: 
+ AI圖片路徑: 為來照片與標記檔案的路徑
+ 群組編號: 用來定位資料集
+ HTML管理報表: 可客製的使用者報表
  
<img width="1913" height="850" alt="image" src="https://github.com/user-attachments/assets/d2aa32b8-d0a0-4c01-8a08-5c937c63aa05" />

## 資料集修改
資料集修改可修改群組與資料集相關內容，「本地路徑」就是照片與標記所儲存的路徑。
<BR>
<BR>
<img width="1920" height="775" alt="image" src="https://github.com/user-attachments/assets/b17654e7-b431-4f23-a345-fdf20243221f" />

+ 資料集主機路徑：網路主機或本地主機資料集所在位置
+ 數量:已標記：所有資料集及已標記資料集占比
+ 類別數量：names的行數也是類別數量
+ 公平性： 此功能是將照片資料集與標註資料集，以7:2:1放置到「train」、「test」、「val」平均分配到「訓練、「測試」、「評估」目錄中，是進行訓練工作的最後一個檢驗程序


<img width="1019" height="393" alt="image" src="https://github.com/user-attachments/assets/2d4ae185-56b0-448d-a519-faaf476235b1" />

## 資料集刪除

選擇群組或資料集可進行資料集刪除。

<img width="588" height="48" alt="image" src="https://github.com/user-attachments/assets/e69d009f-5759-41ee-b228-4d21940ae0bc" />

## 資料集移動
選擇群組或資料集可進行資料集移動位置。
+ 完成度：檢驗標記文字檔(label)、照片檔案、類別names檔案、平均分配資料集、具類別數量的百分比進度條、請完成100%後進行AI模型訓練
+ 下載：將目前標記好的資料集以zip形式打包下載
+ 上傳：可以上傳照片、預標記好的資料集zip檔案上傳到主機


# 第四章: AI資料集標記
資料集群組及資料集新增完畢後，會顯示在左側選單，點選資料集可以顯示資料集照片內容。

<img width="1904" height="957" alt="image" src="https://github.com/user-attachments/assets/9011d6bb-91e3-4827-9cc5-3967f5e60bde" />

## 資料集上傳修改刪除
當完成群組與資料集名稱的建立後，針對某一個資料集，您可點選左側的群組並點選該資料集進行資料集的相關功能設定：

+ 照片(names)上傳：您可以使用小作家自行編修副檔名為names或labels文字檔案，或新增照片檔案並上傳到主機
+ 照片修改：直接滑鼠點選就可以進行照片資料集的
+ 照片刪除：可以刪除照片與標記檔案
+ 資料集數量：總照片張數

## 資料集標記
本軟體同時支援，四邊形Rect標記及多邊形Poly標記，可以點選多邊形標記，可以切換四邊形及多邊形，同一資料集不能混用。
四邊形標記-這是AI標記的基礎形式，也是YOLO AI標記的一般格式，點選「標記標題」區塊可以進到編修模式。

- 整個物件拖曳-直接拖曳「標記標題」
- 錨點拖曳-拖曳錨點以符合物件大小
- 邊線拖曳-調整標記邊界以符合物件大小

<img width="1920" height="967" alt="image" src="https://github.com/user-attachments/assets/f86e97b9-7e06-430c-8cb0-26aee4256367" />

多邊形標記-這又稱為segmentation，物件語意分析，為YOLO AI標記的進階格式。

⚠️ 點選下圖，YouTube影片播放

[![觀看影片](https://img.youtube.com/vi/Nrf-e5iCbkg/0.jpg)](https://www.youtube.com/watch?v=Nrf-e5iCbkg)

- 整個物件拖曳-直接拖曳「標記標題」
- 錨點拖曳-拖曳錨點以符合物件大小

<img width="1920" height="964" alt="image" src="https://github.com/user-attachments/assets/4a405bbe-71bd-463e-a478-54a724b04ba9" />

## 開始標記
欲標記某個物種，請先選擇「標籤清單」內的物種，在照片上的該物種請使用滑鼠點選拖曳，來進行物種標記，標記檔案會自動儲存在主機端。

+ 選擇刪除: 點選「標記標題」，物件進入編輯模式，點選「選擇刪除」按鈕可以將該物件刪除。
+ 刪除所有: 點選「刪除所有」按鈕，可以將整張照片內的物種刪除。
+ 刪除所有ID為: 當您要刪除整個專案的某個ID編號物種，可以先選擇「標籤清單」再點選「刪除所有ID為」按鈕，可以完全刪除整個資料集被選的「標籤清單」物種。
+ 更換所有ID: 將您選擇的的某個ID編號物種，以「標籤清單」選擇的編號進行整個資料集的更換。
  
<img width="1236" height="617" alt="image" src="https://github.com/user-attachments/assets/6c2bfe74-2cd5-4d44-89da-62d0b9af92d5" />

## 標籤清單
標籤清單是以YOLO names或YAML檔案為基礎的物件名稱與ID編號對應檔案，在標記一個物種的代號。

+ YOLO names: 可以在AI資料集設定-> 資料集 -> data.names看到內容。
+ YAML: 可以在AI資料集設定-> 資料集 -> data.yaml看到內容。

<img width="1816" height="482" alt="image" src="https://github.com/user-attachments/assets/287da6fa-0b16-4868-aad3-8ed41b311aed" />

⚠️ 標籤清單僅支援英文。

# 第五章 模型訓練
在完成[CUDA安裝後](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_cuda_ok.jpg)，可以參閱「環境設定套件總覽」。並按下「套件總覽」按鈕，來確定相關套件是否安專完成，如下圖代表套件安裝完成。

![Cuda OK](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_cuda_ok.jpg)

接下來，請安裝YOLO模型。

## YOLO 模型安裝
請至「AI模型訓練」選單，選擇您想要的AI模型，並點選「引擎安裝」按鈕，來下載該模型引擎。

⚠️ 請確保您的標記主機連線到Internet，才可下載模型引擎。

按照步驟將YOLO相關引擎安裝完成，供未來訓練模型時使用。

![安裝YOLO](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_setup.jpg)

## 訓練指令
若您是使用Command指令的使用者，您可以點選「訓練指令」按鈕，來複製Command指令。

## 模型訓練
欲訓練YOLO AI模型，您可以點選「開始訓練」按鈕，進行模型訓練。

週期Epoch: 是訓練週期，一般而言請先點選25或50 Epoch，進行快速訓練，您可以在未來的時間進行長時間的迭代訓練，提昇[F1 score](https://zh.wikipedia.org/zh-tw/F-score)。

![訓練YOLO](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_training.jpg)

## 群組合併訓練
![combined](https://github.com/aailixir/chinese_usermanual/blob/main/images/deme_combined.jpg)

# 第六章 模型版本管理
在訓練完您的第一個YOLO模型後，AI YOLO模型會存在於「模型版本管理」選單內，您可進行:

## 模型報表審視
系統會自動生成詳細的訓練報表，包含：

* 辨識標記分佈圖 <BR>
* 辨識測試結果 <BR>
* F1 Score 曲線 <BR>
* 混淆矩陣 (Confusion Matrix) <BR>

![模型報表](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_release1.jpg)

![模型報表2](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_release2.jpg)

## 模型再次訓練
若您覺得模型準度不理想，您可以點選「再次訓練」按鈕，進行迭代訓練。

![再次訓練](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_again.jpg)

## 照片預標記
您可以再次上傳照片資料集進行預標記，此一功能可以新增更多樣的照片進行AI模型的驗證，YOLO AI要準確要有種不同角度的標記，讓AI模型學習多樣性，一般而言一個辨識物種300會辨識，3000~3萬張會準確。提供辨識不準並修正其標記的多樣性資料集，可以增加模型準度。

![Upload](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_upload.jpg)

# 版權聲明
本網站/程式由 Apache HTTP Server 提供服務，並使用 PHP 程式語言開發。 <BR>
© 2026 胡斯科技有限公司。保留所有權利。 <BR>
本程式碼及相關文件僅供學習與研究用途，未經授權不得複製、散佈或用於商業用途。若需引用或修改，請保留原始作者資訊及本版權聲明。 <BR>
Apache HTTP Server 為 Apache Software Foundation 的開源專案。 <BR>
PHP 為 The PHP Group 所開發並維護的開源程式語言。 <BR>
兩者均依各自的授權條款 (Apache License 2.0 與 PHP License) 使用。 <BR>
 
本專案僅在合法授權範圍內使用上述軟體，並不代表與 Apache Software Foundation 或 The PHP Group 有任何附屬或合作關係。 <BR>




















