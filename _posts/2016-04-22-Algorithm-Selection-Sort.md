---
layout: post
title: Algorithm Selection Sort
---

JavaScript로 선택정렬 구현.

중첩 for 문을 통해 최저값을 찾은 후 swap 한다.

```javascript
var selectionSort = function (arr) {
	var i,
	j,
	minIdx,
	temp,
	len = arr.length;

	if (arr.length < 2) {
		return arr;
	}

	for (i = 0; i < len; i++) {
		minIdx = i;
		for (j = i + 1; j < len ; j++) {
			if (arr[minIdx] > arr[j]) {
				minIdx = j;
			}
		}

		if (i !== minIdx) {
			temp = arr[i];
			arr[i] = arr[minIdx];
			arr[minIdx] = temp;
		}
	}

	return arr;
};

var input = [9,1,7,2,5];
console.log(selectionSort(input)); // [1, 2, 5, 7, 9]
```

중첩 for 문 사용은 버블소팅과 같지만, swap은 빈도는 최대 배열의 총 길이만큼만 발생하기에 조금 더 효율적임
