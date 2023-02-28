背單字小工具
==========
## 主頁
### 能夠選擇要練習的單字表
* 單字表總共有四份，皆是高一時英文雜誌及課本的單字 透過超連結轉換至其他頁面
## 單字頁
### 隨機出題
* 建立一個rand陣列來當作出題時的索引值，rand陣列存放0到題庫長度-1的隨機不重複值
```js 
for (var i = 0; i < q.length; i++) {
	var k = getRandom(q.length);  //取的0到題庫長度-1的隨機數
	rand.push(k);                
	emerge[k] = 1;                //紀錄已出現過防止重複
};
```
### 點擊changeLanguage按鈕選擇要回答英文或是中文
* 透過計數器的奇偶判斷是變成何種語言，接著遍歷題目及答案陣列，使用一temp變數將其互換
```js
if (change % 2 != 0) { //若計數器change是奇數，改成回答中文
//switchToCH
	for (var i = 0; i < ans.length; i++) {
		var temp = ans[i];
		ans[i] = q[i];
		q[i] = temp;
		}
	change++;
	alert("U have changed the language to CH");
}
else {                //若是偶數，改回回答英文
  //switchBackToEN
	for (var i = 0; i < ans.length; i++) {
		var temp = ans[i];
		ans[i] = q[i];
		q[i] = temp;
	}
	alert("U have changed the language to EN");
		cange++;
   }
```
### 在輸入框輸入"skip"跳至下一題
* 若input等於"skip"，break此題迴圈，跳至下題，將此題索引值紀錄在mis陣列
```js
if (input == "skip") {
  mis[rand[i]] = 1;
	break;
}
```
### 在輸入框輸入"skipall"跳至結束
* 將此題開始到結束的題目索引值都記錄至mis陣列，並結束出題迴圈
```js
else if (input == "skipall") {
	for (var i = 0; i < ans.length; i++) {
	  mis[i] = 1;
	}
	break loop1;
  }
```
### 在輸入框輸入"break"結束答題
* 不做任何操作，直接結束出題迴圈
```js
else if (input == "break") {
	break loop1;
}
```

