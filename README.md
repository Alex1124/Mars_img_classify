# Mars_img_classify
Mars orbital image (HiRISE) labeled data set version 3.2 to classify

資料集來源:
https://zenodo.org/record/4002935#.Y_2-l3ZBxhE

類別:
['other', 'crater', 'dark dune', 'slope streak', 'bright dune', 'impact ejecta', 'swiss cheese', 'spider']

類別介紹:

* Bright dune and dark dune are two sand dune classes found on Mars. Dark dunes are completely defrosted, whereas bright dunes are not. Bright dunes are generally bright due to overlying frost and can exhibit black spots where parts of the dune are defrosting.

* The crater class consists of crater images in which the diameter of the crater is greater than or equal to 1/5 the width of the image and the circular rim is visible for at least half the crater's circumference.

* The slope streak class consists of images of dark flow-like features on slopes. These features are believed to be formed by a dry process in which overlying (bright) dust slides down a slope and reveals a darker sub-surface.

* Impact ejecta refers to material that is blasted out from the impact of a meteorite or the eruption of a volcano. We also include cases in which the impact cleared away overlying dust, exposing the underlying surface. In some cases, the associated crater may be too small to see. Impact ejecta can also include lava that spilled out from the impact (blobby ("lobate") instead of blast-like), more like an eruption (triggered by the impact). Impact ejecta can be isolated, or they can form in clusters when the impactor breaks up into multiple fragments.

* Spiders and Swiss cheese are phenomena that occur in the south polar region of Mars. Spiders have a central pit with radial troughs, and they are believed to form as a result of sublimation of carbon dioxide ice. This process can produce mineral deposits on top, which look like dark or light dust that highlights cracks in the CO2 ice.  Spiders can resemble impact ejecta due to their radial troughs, but impact ejecta tends to have straight radial jets that fade as they get farther from the center.  The spider class also includes fan-like features that form when a geyser erupts through the CO2 layer and the material is blown by the wind away from the cracks. Fans are typically unidirectional (following the wind direction), whereas impact ejecta often extends in multiple directions. Swiss cheese is a terrain type that consists of pits that are formed when the sun heats the ice making it sublimate (change solid to gas).

* Other is a catch-all class that contains images that fit none of the defined classes of interest. This class makes up the majority of our data set.


使用Pytorch實作:
* CNN殘差網路
* 資料擴增
  * 方法一: 將所有擴增效果包裹在一個組合，讓效果隨機影響資料，進行擴增
  * 方法二: 缺點很吃效能與大量時間，將各個擴增效果，讓資料集分別擴增厚，在合併，優點資料集擴增很全面，且資料量多足夠機器學習圖片模式。
* 自訂客製化資料集類別
* resnet18遷移式學習
* 凍結層數只訓練FC層
* 演算法嘗試Adam、Nadam
* 學習率嘗試StepLR、ReduceLROnPlateau、OneCycleLR
* 訓練時使用提早結束學習，儲存最佳模型結果

遇到問題:
Q1.混淆矩陣顯示多類別的Precision、Recall在某些類別極糟?

A1.因為特定類別極多，其他類別都很少，因此導致訓練其他類別不佳。將公開資料集二個版本合併，使其他類別數量增加讓演算法可以學到圖片模式


