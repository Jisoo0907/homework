## Avatars 과제

> float을 이용한 이미지 배치  
> flex 지원 환경의 다른 레이아웃 배치  
> 제출: 5월 4일

## Avatars Structure

avatars  
┣ avatars.css  
┣ avatars.html  
┗ avatars.md

## 어려웠던 점

- float 사용 시 가운데 정렬하는 방법
- main에 width 값을 주지 않고 margin: 0 auto;값을 줘서 한참 헤맴
- float 사용해서 두 줄로 정렬하는 방법
- 처음에 이미지 사이에 div를 넣어서 그 div에 clear: both;값을 줬었음
- 더 간결한 방법 발견 => 두 번째 줄에 배치할 첫 사진에 clear: left; 해준 후 float: left; 적용
- 이미지 사이 margin 값 20px 유지하는 법
- on/offline 표시하는 div로 인해 20px보다 늘어남
