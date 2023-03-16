# 17livepretest

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



#### 題目一
/src/components/listComponent.vue

#### 題目二
/src/components/dishRecipe.vue

#### 3-1 請說明 Flux, Redux, Vuex 之間的差異
Flux是個設計模式，Redux/Vues都是基於他設計。
三者都有資料唯讀性的特點，也就是資料只能被讀取不能被直接修改
###### Flux/Redux
Flux與Redux比較接近，在state需要被修改時會透過回傳一個新的state來替換舊的state，Flux/Redux依照判斷是否為新的state來決定是否需要更新畫面，而新的與舊的state因為其記憶體位置不同故能判斷是否為更新。
###### Vuex
則是以mutation方式去修改state本身，而當state的值被更新，也會同步更新到畫面上。

#### 3-2 請說明單向資料流與雙向資料流在處理資料更新上的異同
單向資料流主要是parent->child的單向資料傳遞，vue/react中都是使用props
方式由上到下傳遞資料。
雙向則是 除了parent->child 還有child->parent。
而雙向資料流更新資料的方式不是把parent傳遞下來的props值直接拿來做修改，因為如果直接修改會造成管理上的困難，系統架構變大時會很難追蹤哪些child修改過變數。
###### Vue
在vue中若需要修改parent傳遞過來的資料需要透過emit event的方式回傳給parent (而在parent中需要傳遞一個event 給child以讓child可以執行emit)。

###### React
在React是從parent傳遞一個callback function工child執行，在callback function中帶入要被修改的值。


#### 3-3 這些設計主要想要解決什麼樣的問題? 優缺點為何?
##### 3-1 state managment
雖然如vue/React中已經有雙向資料流可以讓parent-child傳遞資料，但是當資料路徑傳遞距離太遠時，就會有管理上的困難，找尋某個資料的源頭就需要一路溯源回去變得非常沒有效率。
使用Flux/Redux/Vuex要解決這個問題，而這些方法是透過中央管理的方式，統一管理資料狀態，
###### 優點
多個component都可以輕易取得資料，不需要再透過資料流的方式傳遞資料。
集中管理更容易維護，能較準確的預測狀態的變化，而且也有devTool可以觀察狀態
###### 缺點
1. 小型專案可能不適用，可能會增加更多的開發成本，或許使用單雙向數據流即可解決資料存取問題
2. 資料不一致性，當多個元件存取相同的state，可能會有資料不一致的問題

##### 3-2雙向單向資料流
雙向資料流主要像要解決單向資料流在child 與 parent資料要同步更新的問題，單向資料流的好處是容易管理、較少的錯誤發生。
但是有時候某些資料是從child取得，同時也需要傳遞給parent，此時就需要使用雙向資料流，vue/react都有類似的方式去傳遞資料，其優點是容易看出有哪些child的有使用emit event(vue)/callback function(react)，相對也較好管理，但是在設計時也要謹慎，以免產生錯誤(例如：循環更新、多個component更新造成資料不一致)
