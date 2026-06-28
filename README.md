# 第一章: 使用前準備
## 軟體安裝
請下載AI靈丹軟體安裝包，使用滑鼠雙敲執行安裝Ailixir AI靈丹軟體。

<img width="648" height="448" alt="image" src="https://github.com/user-attachments/assets/55c3708e-7c4b-460a-89bc-019e4777143f" />

## 版權聲明
本網站/程式由 Apache HTTP Server 提供服務，並使用 PHP 程式語言開發。

© 2025 胡斯科技有限公司。保留所有權利。

本程式碼及相關文件僅供學習與研究用途，未經授權不得複製、散佈或用於商業用途。
若需引用或修改，請保留原始作者資訊及本版權聲明。

Apache HTTP Server 為 Apache Software Foundation 的開源專案，
PHP 為 The PHP Group 所開發並維護的開源程式語言。
兩者均依各自的授權條款 (Apache License 2.0 與 PHP License) 使用。

本專案僅在合法授權範圍內使用上述軟體，並不代表與 Apache Software Foundation 或 The PHP Group 有任何附屬或合作關係。

## 訓練主機需求
作業系統：Windows 10、Windows 11
GPU需求：RTX20系列、RTX30系列、RTX40系列、RTX50系列
記憶體RAM：4GB以上

# 第二章: 開始使用
安裝完畢後，請使用瀏覽器並輸入網址如下：
http://127.0.0.1:8080
http://localhost:8080 

您可以輸入預設使用者名稱及密碼：

	使用者名稱：demo@example.com
	密碼：demo

輸入完使用者名稱及密碼後，請點選「登錄」鍵。


<img width="1920" height="963" alt="image" src="https://github.com/user-attachments/assets/8a00ce62-53ad-40f2-a202-8ed6dc68ef31" />


# 第三章: AI資料集介紹
影像AI資料集是照片圖檔的集合，標注資料集(txt文字檔)則是教導AI的一個過程，如下圖所示為事先標記好的資料集。 

註：照片圖檔僅支援 jpg、jpeg、png、bmp格式

## AI資料集設定畫面

<img width="1906" height="954" alt="image" src="https://github.com/user-attachments/assets/f056a99b-c7d4-47fe-889f-a70e509bcf72" />

## AI資料集設定
請先點選左邊的導覽選單「AI資料集設定」進行「群組」及「資料集」設定，點選「新增群組」進行群組管理。
點選該新增群組可在該群組下點選「資料集新增」按鈕。新增完資料集後可以開始建立資料集。群組為相同的資料集, 共享統樣的物件種類(names檔案)。

## 資料集群組新增
請輸入群組名稱來建立群組。

<img width="1920" height="479" alt="image" src="https://github.com/user-attachments/assets/840c638e-cf99-40a1-97f0-544963f23c1a" />

## 資料集新增
+ 資料集名稱: 可以用來記錄辨識用
+ 群組名稱: 
+ AI圖片路徑: 為來照片與標記檔案的路徑
+ 群組編號: 用來定位資料集
+ HTML管理報表: 可客製的使用者報表
  
<img width="1913" height="850" alt="image" src="https://github.com/user-attachments/assets/d2aa32b8-d0a0-4c01-8a08-5c937c63aa05" />

## 資料集修改
<img width="1920" height="775" alt="image" src="https://github.com/user-attachments/assets/b17654e7-b431-4f23-a345-fdf20243221f" />

+ 資料集主機路徑：網路主機或本地主機資料集所在位置
+ 數量:已標記：所有資料集及已標記資料集占比
+ 類別數量：names的行數也是類別數量
+ 公平性： 此功能是將照片資料集與標註資料集，以7:2:1放置到「train」、「test」、「val」平均分配到「訓練、「測試」、「評估」目錄中，是進行訓練工作的最後一個檢驗程序


<img width="1019" height="393" alt="image" src="https://github.com/user-attachments/assets/2d4ae185-56b0-448d-a519-faaf476235b1" />


+ 完成度：檢驗標記文字檔(label)、照片檔案、類別names檔案、平均分配資料集、具類別數量的百分比進度條、請完成100%後進行AI模型訓練
+ 下載：將目前標記好的資料集以zip形式打包下載
+ 上傳：可以上傳照片、預標記好的資料集zip檔案上傳到主機




+ AI資料集：資料集名稱
+ 標記名稱：這裡是包含了YOLO框架物件名稱，是以文字檔格式來代表物件名稱，每一行一個物種名稱，並須以英文來表示。



## 3.2	資料集設定
當完成群組與資料集名稱的建立後，針對某一個資料集，您可點選左側的群組並點選該資料集進行資料集的相關功能：

+ 照片(names)上傳：您可以使用小作家自行編修副檔名為names或labels文字檔案，或新增照片檔案並上傳到主機
+ 照片修改：直接滑鼠點選就可以進行照片資料集的
+ 照片刪除：
+ 模擬播放：













