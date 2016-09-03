---
layout: post
title: JavaScript Module Pattern
---

__Module Pattern__ is a software design technique to seperate functionality of a large software program into independant small pieces, __*modules*__.

```javascript
var countModule = (function () {
	var count_ = 0;

	return {
		getCount : function () {
			return count_;
		},
		increaseCount : function () {
			count_++;
		},
		decreaseCount : function () {
			count_--;
		},
		resetCount : function () {
			count_ = 0;
		}
	};
})();

countModule.increaseCount();
countModule.getCount(); // 1

countModule.decreaseCount();
countModule.decreaseCount();
countModule.getCount(); // -1

countModule.resetCount();
countModule.getCount(); // 0
```