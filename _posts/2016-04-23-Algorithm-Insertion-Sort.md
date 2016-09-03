---
layout: post
title: Algorithm Insertion Sort
---

JavaScript로 삽입정렬 구현.

배열의 첫번째 엘리멘트를 정렬됐다 가정하고 두번째 엘리멘트부터 배열 끝까지 정렬된 엘리멘트들와 비교하여 적절한 위치에 삽입한다.

1. 배열 2번째 엘리멘트부터 끝까지 반복.
2. 현재 엘리멘트를 1번 과정의 인자로 설정.
3. 이전과 현재 엘리멘트를 비교.
    2.1. 이전 엘리멘트가 크면 swap, 2번 과정으로 이동.
    2.2. 아니면 1번 과정으로 이동.

```javascript
var insertionSort = function (arr) {
	if (arr.length < 2) {
		return arr;
	}

	var i,
	j,
	curIdx,
	temp,
	len = arr.length;
	for (i = 1; i < len; i++) {
		curIdx = i;
		for (j = i - 1; j >= 0; j--) {
			if (arr[j] > arr[curIdx]) {
				temp = arr[j];
				arr[j] = arr[curIdx];
				arr[curIdx] = temp;
				curIdx--;
			} else {
				break;
			}
		}
	}

	return arr;
};

var input = [9,1,7,2,5];
console.log(insertionSort(input)); // [1, 2, 5, 7 ,9]
```

다음에 안쪽 for문을 while 로 다시 작성해 보도록.