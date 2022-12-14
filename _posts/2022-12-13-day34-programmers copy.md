---
title:  "프로그래머스 Lv.1 Day 34"
excerpt: "자바(java) - 최소직사각형"

categories:
  - Programmers
tags:
  - [Blog]

toc: true
toc_sticky: true
 
date: 2022-12-13
last_modified_at: 2022-12-13
---

#### 34. 최소직사각형


- **문제 설명** 

명함 지갑을 만드는 회사에서 지갑의 크기를 정하려고 합니다. 다양한 모양과 크기의 명함들을 모두 수납할 수 있으면서, 작아서 들고 다니기 편한 지갑을 만들어야 합니다. 이러한 요건을 만족하는 지갑을 만들기 위해 디자인팀은 모든 명함의 가로 길이와 세로 길이를 조사했습니다.

아래 표는 4가지 명함의 가로 길이와 세로 길이를 나타냅니다.

|**명함 번호**|**가로 길이**|**세로 길이**|
|:---:|:---:|:---:|
|1|60|50|
|2|30|70|
|3|60|30|
|4|80|40|




가장 긴 가로 길이와 세로 길이가 각각 80, 70이기 때문에 80(가로) x 70(세로) 크기의 지갑을 만들면 모든 명함들을 수납할 수 있습니다. 하지만 2번 명함을 가로로 눕혀 수납한다면 80(가로) x 50(세로) 크기의 지갑으로 모든 명함들을 수납할 수 있습니다. 이때의 지갑 크기는 4000(=80 x 50)입니다.

모든 명함의 가로 길이와 세로 길이를 나타내는 2차원 배열 sizes가 매개변수로 주어집니다. 모든 명함을 수납할 수 있는 가장 작은 지갑을 만들 때, 지갑의 크기를 return 하도록 solution 함수를 완성해주세요.


- **제한사항**

sizes의 길이는 1 이상 10,000 이하입니다.
sizes의 원소는 [w, h] 형식입니다.
w는 명함의 가로 길이를 나타냅니다.
h는 명함의 세로 길이를 나타냅니다.
w와 h는 1 이상 1,000 이하인 자연수입니다.

- **입출력 예**

|**sizes**|**result**|
|:---:|:---:|
|[60, 50], [30, 70], [60, 30], [80, 40]|4000|
|[10, 7], [12, 3], [8, 15], [14, 7], [5, 15]|120|
|[14, 4], [19, 6], [6, 16], [18, 7], [7, 11]|133|



- **My Solution**

```java
class Solution {
    public int solution(int[][] sizes) {
        int answer = 0;
        int max_w = 1;
        int max_h = 1;
        
        for(int i=0; i<sizes.length; i++) {
            int long_len = Math.max(sizes[i][0], sizes[i][1]);
            int short_len = Math.min(sizes[i][0], sizes[i][1]);
            
            if(long_len > max_w) {
                max_w = long_len;
            }
            
            if(short_len > max_h) {
                max_h = short_len;
            }
        }
        
        return answer = max_w * max_h;
    }
}
```

⭐ 우선 문제를 해석해보면 각 명함마다 가로와 세로의 길이를 비교해보고 큰 값을 가로로, 작은 값을 세로로 이동해줘야한다. 그 후 주어진 명함의 가로길이와 세로길이의 최댓값을 구하여 곱해주면 모든 크기의 명함을 수납할 수 있는 지갑을 만들 수 있다.

자바의 기본 java.lang.Math클래스 안의 메서드 중 최댓값과 최솟값을 구해주는 메서드가 있어서 그것을 이용해봤다. 가로와 세로의 길이는 1이 최솟값이므로 최댓값을 담아줄 변수를 선언해줘 1로 초기화했다. 그리고 Math.max(), Math.min() 메소드를 이용하여 각각 가로의 최댓값, 세로의 최댓값을 구해줬다. 최종적으로 이 두 값을 곱해주면된다.


**프로그래머스 Lv.1 Day 34. 최소직사각형 - 자바(java)**