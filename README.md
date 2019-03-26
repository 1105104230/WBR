# 人臉辨識系統
## 安裝套件
#### 若已經在anaconda的環境下，只需要在安裝(pip) imutils、cv2
---
## *collect-faces.py*
#### 首先，這個程式是透過電腦的鏡頭(或外接的)，來擷取人臉的影像，方便後面*電腦的影像比對*時的重要數據。
##### 下面這一行程式，這是擷取下來的影像所存放的 *資料夾*(請記得和這個.py檔同一個*路徑*)
```
savePath = "collected"
```
---
## *extract-faces.py*
#### 這個.py檔，是將本身圖庫的圖片，去做人臉辨識，自動修幅成*電腦的影像比對*可以用的照片
##### 下面這行程式，這是未修幅的照片的 *資料夾*(請記得和這個extract-faces.py檔同一個*路徑*)
```
sourePath = "mama"
```
##### 下面這行程式，這是修幅過後的照片 *資料夾*(請記得和這個extract-faces.py檔同一個*路徑*)
```
savePath = "okok"
```
##### 下面這行程式，是調整修幅後照片的大小
```
face_size_min = (47, 62)
```
---
## *train.py*
#### 利用不同的人，利用*extract-faces.py*、*collect-faces.py*收集的照片，進行機器訓練，這是這個整個model最精華的程式，實踐了機器學習的部分，雖然很陽春XD
#### 先把彩色照片一張張灰階後，原本R、G、B都是255pixel的照片，瞬間變成只有黑跟白的輪廓的照片，方便電腦更好也更快速的進行 *二分法*的比對(不要動這幾行程式)
```
for (i, imagePath) in enumerate(imagePaths):
		# load the image and convert it to grayscale
		print(imagePath)
		face = cv2.imread(imagePath)
		face = cv2.cvtColor(face, cv2.COLOR_BGR2GRAY)
		face = cv2.resize(face, face_size)
```
#### 下面這行程式是要比對照片的資料夾，記得不同的人要先手動分類成不同的資料夾喔!!
```
facePath = "datasets"
```
#### 下面這行程式是一個人比對照片的最少數量，每個人的照片都要達到此數量，程式才會進行比對喔
```
faces_min = 15
```
#### 比對完會產生兩個檔案，一個是名字的標籤檔(不重要)，而另一個是比對完數據的權重檔(檔案比較大的那個就是)
---
## 未完待續
---
