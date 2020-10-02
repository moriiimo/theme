
## theme

Android 11 Meetups 第8回 UI、デザインの回で発表した「Jetpack Composeに備えてMaterial Design対応をおさらいする」の内容のサンプルです。  
指摘点などありましたらお気軽に :bow:  

## 構成
![image](https://user-images.githubusercontent.com/2480781/94897738-39d40300-04cb-11eb-8308-040c08c33f2b.png)

### [theme](https://github.com/moriiimo/theme/blob/master/app/src/main/res/values/theme.xml)
- アプリのデザインソースになる設定を記載
- Theme, ThemeOverlay以外は記載しない

### [color](https://github.com/moriiimo/theme/blob/master/app/src/main/res/values/colors.xml)
- アプリの色を定義する
- 色そのものを表す命名にする
- alpha値のある値は、[color](https://github.com/moriiimo/theme/tree/master/app/src/main/res/color)フォルダ下にColorStateListを作るとよさそう
- レイアウトファイルなどから直接参照されないように注意

### [type](https://github.com/moriiimo/theme/blob/master/app/src/main/res/values/types.xml)
- TextAppearance系をまとめる
- デフォルトから変更がなくても、作成してThemeに設定しておくといいかもしれない

### [shape](https://github.com/moriiimo/theme/blob/master/app/src/main/res/values/shapes.xml)
- ShapeAppearance系をまとめる
- [こちらのドキュメント](https://material.io/develop/android/theming/shape)が元です

### 実行時のイメージ
Main|Sub
------------ | -------------
![device-2020-10-02-164412](https://user-images.githubusercontent.com/2480781/94899787-dcda4c00-04ce-11eb-9a6e-1e51e84e881a.png)|![device-2020-10-02-165500](https://user-images.githubusercontent.com/2480781/94900631-44dd6200-04d0-11eb-931e-29149cc8f9b3.png)


## Meetups中にいただいた質問
### デザイナーからの資料がattributeを意識していない場合どのような対応をするのがベストか
実装側がまずざっくりattributeにマッピングして、外れるものとattributeになるものを決めてしまって、  
それをもとにデザイナーさんとコミュニケーションしてみる  
新しい画面などで新規の色が出てきたら、これ同じ用途でまとまりませんか、というような話をするなど  
Themeにattributeとして記載するかどうかは難しいところだと思いました。。。

### textAppearanceとカラーの組み合わせはすべてstyleで設定してから利用するべきか
対象になるWidgetが、その組み合わせでアプリ全体のデザインソースとしてもよさそうであれば、  
textAppearance+colorを定義したWidgetのstyleを作り、Themeに設定していいんじゃないかと思う  
そうでない場合は、レイアウト上でtextAppearanceとcolorをTheme属性を通して設定するのがいいのではないかと思った。  
そのほうが、Styleタグを残しておけてその後に別のなにかを適用したくなったときに修正が少なくなりそうなため  

## その他
- TextAppearance, ShapeAppearanceなど、定義するときの命名には、それぞれ継承元の名称を含めたほうがわかりやすそうと感じた  
e.g. TextAppearance.Hoge.Subtitle1, ShapeAppearance.Hoge.SmallComponent 