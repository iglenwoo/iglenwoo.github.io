---
layout: post
title: Algorithm Merge Sort
---

JavaScript로 병합정렬 구현.

재귀호출을 통해구현

1. 배열을 반으로 가장 작은 단위까지 나눔
2. 좌항 우항을 비교 후 정렬(합침)
3. 결과 리턴

```javascript
var mergeSort = function (arr) {
	if (arr.length < 2) {
		return arr;
	}

	var mid = Math.floor(arr.length / 2),
	left = mergeSort(arr.slice(0, mid)),
	right = mergeSort(arr.slice(mid));

	var i = 0,
	j = 0,
	result = [];
	while (i < left.length && j < right.length) {
		if (left[i] < right[j]) {
			result.push(left[i++]);
		} else {
			result.push(right[j++]);
		}
	}

	if (left[i]) result.push(left[i]);
	if (right[j]) result.push(right[j]);

	return result;
};

var input = [9,1,7,2,5];
console.log(mergeSort(input)); // [1, 2, 5, 7 ,9]
```

배열이 홀수일 때(ex. [3,1,2] = [3], [1,2]), 병합 시 한 쪽 엘리멘트가 남게됨.
이를 처리하기 위한 로직 변경가능.

```javascript
//	if (left[i]) result.push(left[i]);
//	if (right[j]) result.push(right[j]);
	result.push(left[i] ? left[i] : right[j]);
```

2로 나누어 버림을 하기 때문에 우항만 엘리멘트가 하나 더 있는경우 발생할듯.
고로, 우항만 봐도 될듯함.

```javascript
//	if (left[i]) result.push(left[i]);
	if (right[j]) result.push(right[j]);
```