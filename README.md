# MK's Cartoon Rendering

## 📌 개요
이 프로그램은 OpenCV를 사용하여 내가 원하는 이미지를 만화(cartoon) 스타일로 변환하는 프로그램입니다.   

## :memo: 기능 소개
- ✅ **이미지 스타일 변환**
```python
 # 이미지 로드
 img = cv2.imread('img.png')

 # 이미지를 회색 스케일로 변환
 gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

 # 노이즈를 줄이기 위해 중앙값 블러 적용
 gray = cv2.medianBlur(gray, 5)

 # 적응형 임계값을 사용하여 가장자리 감지
 edges = cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 9, 9)

 # 이미지를 컬러 이미지로 변환
 color = cv2.bilateralFilter(img, 9, 300, 300)

 # 컬러 이미지와 가장자리 마스크를 결합
 cartoon = cv2.bitwise_and(color, color, mask=edges)

 # 만화 이미지 표시
 cv2.imshow("Cartoon", cartoon)
 cv2.waitKey(0)
 cv2.destroyAllWindows()
```
## :o: 만화같은 느낌이 잘 표현되는 이미지
<img src="https://github.com/Mean-Key/MK_CV_CR/blob/main/img/character.png" width="300" height="200"/> &rarr; <img src="https://github.com/Mean-Key/MK_CV_CR/blob/main/img/character-cr.png" width="300" height="200"/>


## :x: 만화같은 느낌이 잘 표현되지 않는 이미지


## :heavy_exclamation_mark: 알고리즘의 한계점
