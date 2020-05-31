Zaczynamy pracę z projektem przez implementację biblioteki:

`import cv2`

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
Załadowanie zdjęcia i przekształcenie go do odcieni szarości

```
img = cv2.imread("Resources/lena.png")
imgGray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)

cv2.imshow("Gray Image", imgGray)
cv2.waitKey(0)
```