Zaczynamy pracę z projektem przez implementację bibliotek:

```
import cv2
import numpy as np
```

**Podstawowe czynności:**

Wyświetlanie zdjęcia

```
img = cv2.imread("Resources/lena.png")
cv2.imshow("Output", img)
```

Wyświetlanie wideo

```
cap = cv2.VideoCapture("Resources/test_video.mp4")
 while True:
     success, img = cap.read()
     cv2.imshow("Video",img)
     if cv2.waitKey(1) & 0xFF ==ord('q'):
         break
```
         
         
Wyświetlanie obrazu z kamerki internetowej, po naciśnięciu "Q" wyłącza się okno

```
cap = cv2.VideoCapture(0)
cap.set(3, 640)
cap.set(4, 480)
while True:
    success, img = cap.read()
    cv2.imshow("Video", img)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
```
Załadowanie zdjęcia i przekształcenie go kolejno przez filtry:
* odcienie szarości
* rozmycie Gaussa
* kontury
* rozpikselizowanie
* wyostrzenie

```
img = cv2.imread("Resources/lena.png")
kernel = np.ones((5,5),np.uint8)
imgGray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
imgBlur = cv2.GaussianBlur(imgGray,(7,7),0)
imgCanny = cv2.Canny(img, 150, 200)
imgDilation = cv2.dilate(imgCanny, kernel, iterations=1)
imgEroded = cv2.erode(imgDilation, kernel, iterations=1)

cv2.imshow("Gray Image", imgGray)
cv2.imshow("Blur Image", imgBlur)
cv2.imshow("Canny Image", imgCanny)
cv2.imshow("Dilation Image", imgDilation)
cv2.imshow("Eroded Image", imgEroded)
cv2.waitKey(0)
```

Sprawdzanie rozmiaru danego obrazu i skalowanie go
```
print(img.shape)
imgResize = cv2.resize(img,(300,300))
```