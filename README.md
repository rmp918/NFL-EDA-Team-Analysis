# NFL-EDA-Team-Analysis

## 前言
  大家好，這篇是針對Kaggle上的NFL Big Data Bowl 2021資料集做視覺化分析。我會分成三個章節作介紹，分別是介紹NFL、敘述性統計、球賽資料視覺化。透過這三個章節，我希望能讓正在看這篇分析的你對NFL有更多的認識，也可以從中找到球賽中的奧妙。
  
  由於大部分的圖都是使用plotly這個package做視覺化，可惜的是該package最強的功能 「與使用者互動」，無法呈現在github上。
因此附上連結，讓讀者可以透過 kaggle kernal 的方式完整體驗這些圖表。

https://www.kaggle.com/rmp918/nfl-eda-team-analysis

## 一. NFL介紹
  國家美式足球聯盟（英語：National Football League，縮寫為NFL）是世界最大的職業美式足球聯盟，也是世界最具商業價值的體育聯盟之一。聯盟最早在1920年以美國職業美式足球協會（American Professional Football Association）成立，於1922年1月28日改名為國家美式足球聯盟（National Football League）。國家美式足球聯盟是北美四大職業運動之一。

  目前聯盟共有32支球隊，分為兩個聯會：美國美式足球聯會和國家美式足球聯會，每個聯會由四個分區組成，每個分區有四支球隊。在例行賽季中，每支球隊於每年9月至12月間、共17週內實行16場比賽，比賽日通常選在週日、週一或週四。例行賽季後，每個聯會共有七支球隊進入季後賽，包括各分區冠軍(4隊)和戰績較佳的3隊(通常稱為外卡（Wild Card）隊)。經過三輪淘汰賽，兩個聯會的冠軍在預定球場舉辦超級盃比賽，爭奪最後的總冠軍。超級盃舉辦前一周，會在奧蘭多舉辦職業盃明星賽，由兩聯會各選出明星選手。[資料來源:wiki]
  
  而目前的32支球隊(依照官方聯會分區分組)有:
  
  AFC_East: Buffalo Bills, Miami Dolphins, New England Patriots, New York Jets
  
  AFC_West: Denver Broncos, Kansas City Chiefs, Las Vegas Raiders, Los Angeles Chargers
  
  AFC_North: Baltimore Ravens, Cincinnati Bengals, Cleveland Browns, Pittsburgh Steelers
  
  AFC_South: Houston Texans, Indianapolis Colts, Jacksonville Jaguars, Tennessee Titans
  
  NFC_East: Dallas Cowboys, New York Giants, Philadelphia Eagles, Washington Football Team
  
  NFC_West: Arizona Cardinals, Los Angeles Rams, San Francisco 49ers, Seattle Seahawks
  
  NFC_North: Chicago Bears, Detroit Lions, Green Bay Packers, Minnesota Vikings
  
  NFC_South: Atlanta Falcons, Carolina Panthers, New Orleans Saints, Tampa Bay Buccaneers
  
  最後是要介紹一支橄欖球隊的球員位置，會分成進攻組跟防守組




