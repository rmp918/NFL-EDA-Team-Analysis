# NFL-EDA-Team-Analysis

## 前言
  大家好，這篇是針對Kaggle上的NFL Big Data Bowl 2021資料集做視覺化分析。我會分成三個章節作介紹，分別是介紹NFL、敘述性統計、球賽資料視覺化。透過這三個章節，我希望能讓正在看這篇分析的你對NFL有更多的認識，也可以從中找到球賽中的奧妙。
  
  由於大部分的圖都是使用plotly這個package做視覺化，可惜的是該package最強的功能 「與使用者互動」，無法呈現在github上。
因此附上連結，讓讀者可以透過 kaggle kernal 的方式完整體驗這些圖表。

https://www.kaggle.com/rmp918/nfl-eda-team-analysis

## 一. NFL介紹
  國家美式足球聯盟（英語：National Football League，縮寫為NFL）是世界最大的職業美式足球聯盟，也是世界最具商業價值的體育聯盟之一。聯盟最早在1920年以美國職業美式足球協會（American Professional Football Association）成立，於1922年1月28日改名為國家美式足球聯盟（National Football League）。國家美式足球聯盟是北美四大職業運動之一。

  目前聯盟共有32支球隊，分為兩個聯會：美國美式足球聯會和國家美式足球聯會，每個聯會由四個分區組成，每個分區有四支球隊。在例行賽季中，每支球隊於每年9月至12月間、共17週內實行16場比賽，比賽日通常選在週日、週一或週四。例行賽季後，每個聯會共有七支球隊進入季後賽，包括各分區冠軍(4隊)和戰績較佳的3隊(通常稱為外卡（Wild Card）隊)。經過三輪淘汰賽，兩個聯會的冠軍在預定球場舉辦超級盃比賽，爭奪最後的總冠軍。超級盃舉辦前一周，會在奧蘭多舉辦職業盃明星賽，由兩聯會各選出明星選手。[資料來源:wiki]
  
  而目前的32支球隊(依照2018NFL官方聯會分區分組的排名)有:
  
  | 分區        | 1                    | 2                    | 3                        | 4                    |
|-----------|----------------------|----------------------|--------------------------|----------------------|
| AFC_East  | New England Patriots | Miami Dolphins       | Buffalo Bills            | New York Jets        |
| AFC_West  | Kansas City Chiefs   | Los Angeles Chargers | Denver Broncos           | Las Vegas Raiders    |
| AFC_North | Baltimore Ravens     | Pittsburgh Steelers  | Cleveland Browns         | Cincinnati Bengals   |
| AFC_South | Houston Texans       | Indianapolis Colts   | Tennessee Titans         | Jacksonville Jaguars |
| NFC_East  | Dallas Cowboys       | Philadelphia Eagles  | Washington Football Team | New York Giants      |
| NFC_West  | Los Angeles Rams     | Seattle Seahawks     | San Francisco 49ers      | Arizona Cardinals    |
| NFC_North | Chicago Bears        | Minnesota Vikings    | Green Bay Packers        | Detroit Lions        |
| NFC_South | New Orleans Saints   | Atlanta Falcons      | Carolina Panthers        | Tampa Bay Buccaneers |
  
  
  
  最後是要介紹一支橄欖球隊的球員位置，會分成進攻組跟防守組以及特別組。
  基本上進攻組會以四分衛為核心，選擇傳球，衝刺等進攻手段，防守組就是以全力阻擋進攻方進攻到達陣區(Touchdown)，特別組則是會在棄踢(Punt)、射門等場合才會出現。
  
  

| 進攻組                           | 防守組                             | 特別組                               |
|-------------------------------|---------------------------------|-----------------------------------|
| 中鋒(Center, C)                 | 防守絆鋒/防守截鋒(Defensive Tackle, DT) | 踢球員(Kicker, K)                    |
| 哨鋒/護鋒(Offensive Guard, OG)    | 防守邊鋒/防守端鋒(Defensive End, DE)    | 控球員/扶球手(Holder, H)                |
| 絆鋒/截鋒(Offensive Tackle, T或OT) | 線衛(Linebacker, LB)              | 棄踢員(Punter)                       |
| 四分衛(Quarterback, QB)          | 角衛(Cornerbacks, CB)             | 回攻員(Kickoff/Punt Returner, KR/PR) |
| 跑衛(Runningback, RB)           | 安全衛(Safety, S)                  | 長開球員(Long Snapper, LS)            |
| 外接員(Wide Receiver, WR)        |                                 | 槍手(Gunner)                        |
| 邊鋒/近端鋒(Tight End, TE)         |                                 |                                   |

  
  每場都是進行四節，每節15分鐘的比賽。持球的一隊（進攻方）有四次進攻機會向前（防守方的端區）推進10碼，每次機會稱為一個「檔」（down，即被對方攔截放倒一次）。當進攻一方成功在四檔內累積推進了10碼（或超過），便可再次獲得繼續進攻的四檔。如果進攻一方在四檔內都不能向前移動10碼，便要把球在第四檔進攻結束的位置交給對手。一般大多會在第四檔時採用棄踢（punt）將球權轉移給對手但令他們必須從較遠的地方開始進攻。一次達陣得6分，達陣後加踢得1分，以跑、傳等方法，再達陣一次，加2分；射門得3分。以上為有關NFL的基礎資訊，有了這些知識後，就可以開始後續的分析。

## 二. 敘述型統計

  這個章節，會透過對球員的身高、位置、畢業學校等基本資訊做視覺化的展現

  首先，我們可以看到大多數球員的身高都落在6尺左右的區間。可以發現到這項運動不像NBA一樣注重身高，球員動輒就是7尺上下的區間。NFL的球員大多是注重速度跟接球的反應能力還有爆發力，這些數據是無法透過身高體重的關係去觀察出來的。也代表在體重方面大部分球員不會太胖，除了一些像是進攻組的中鋒、哨鋒、絆鋒，防守組的絆鋒才會是比較胖比較厚實的(因為要擋住四分衛不受對方夾擊/衝擊四分衛)。

![image](https://github.com/rmp918/NFL-EDA-Team-Analysis/blob/main/image/players_height_distribution.png)
![image](https://github.com/rmp918/NFL-EDA-Team-Analysis/blob/main/image/players_weight_distribution.png)


      
          
      

  







