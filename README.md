# Meteor_search_tool
簡介

這軟體是用來協助搜尋影片中的流星, 主要參考
https://takatsukagaku.com/geosciene-education/meteor-check-program/
修改而成, 如有任何版權問題請告知.

目前還不算完美, 一些飛機/衛星/飛蟲都會偵測到. 而且搜尋速度有點慢, 1.5hr影片大概會花超過3hr.
但已經比人工看輕鬆多就是了XD

主要流程是每取三個frame, 去偵測白點移動, 如果有發現會印LOG+存在excel檔案內. 每500 frame如果有偵測到流星
就會儲存一張圖片. 之後還是需要人工看產生的照片判定是否為流星, 然後再根據圖片檔名去比照excel的紀錄, 看流星在影片的哪個時間點.

Img resize可以降解析度, 在分析上會比較快, 但是如果用廣角鏡拍的影片, 流星很細, 就很容易被吃掉.
所以我都還是保持4K下去跑, 就是花時間.

Threshold_1 主要是轉灰階的時候要保留多亮的部分, 如果拍到的星星偏暗, 就需要調低一點. 但太低會導致雜訊太多, 就會狂誤判.

Threshold_2 是用來判定移動的部分.

Test按了會先跑前50 frame, 可以看一下有沒有狂誤判或是根本看不到星星的問題.
專案內有四個小流星影片, 都需要不同的數值才能偵測到, 可以先試試看手感.

每次Start都會產生新資料夾 output\frame_images_MMDD_HHMMSS 圖片跟excel檔案都會存在這

圖片的檔案名稱就是 時間_composite_FrameNumber.jpg

0901_151715_composite_71500.jpg 這張看起來就會是流星.
![0901_151715_composite_71500](https://github.com/Frogofmagic/Meteor_search_tool/assets/11169420/17d5105d-85d9-4002-96bb-1c91f45494e9)

0901_151715_composite_57500.jpg 這張看起來應該是飛機之類的
![0901_151715_composite_57500](https://github.com/Frogofmagic/Meteor_search_tool/assets/11169420/eb3563d4-f996-4728-8a9a-473c9961e4da)

認定在71500有流星後, 就去excel檔案內找fr = 71000~71500之間的紀錄
![image](https://github.com/Frogofmagic/Meteor_search_tool/assets/11169420/dfb0f639-96ff-4fcf-902e-d6a9396cb8f4)

接著就可以去看影片中00:39:36 應該就會找到流星了.


介面是用PyQT5做的, 不確定為何產生的.exe無法使用, 所以就只有先放.py等檔案.
小弟python新手, 歡迎任何建議:)

之後應該會再結合用影像辨識掃所有產生的照片, 就可以再刪掉那些飛機/相機震動/飛蟲等等的圖片.
最終當然還是希望這工具能順便把影片自動剪好XDDD
