長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
LOL_posts_list <- list()
for(i in 7082:7086){
LOLurl<-paste("https://www.ptt.cc/bbs/LOL/index",i,".html",sep = '')
LOLContent<-read_html(LOLurl)

post_Title <- LOLContent %>%
html_nodes(".title") %>% 
html_text()

post_PushNum <-LOLContent %>%
html_nodes(".nrec")%>%
html_text()

post_Author<-LOLContent%>%
html_nodes(".author")%>%
html_text()

data<-data.frame(title=post_Title,PushNum=post_PushNum,Author=post_Author)
LOL_posts_list[[i]] <- data
}
LOL_dataframe<- rbind(LOL_posts_list[[7082]],LOL_posts_list[[7083]],LOL_posts_list[[7084]],LOL_posts_list[[7085]],LOL_posts_list[[7086]])
```

爬蟲結果呈現
------------

``` r
knitr::kable(LOL_dataframe)
```

| title                                               | PushNum | Author       |
|:----------------------------------------------------|:--------|:-------------|
| \[公告\] 不可能會有人全部看完多人水桶               | 爆      | samhou6      |
| \[實況\] 漢默丁格本人的台                           | 1       | cha7919      |
| \[問題\] 新版競時通+50%能量 4勝加成與一日加成       | 20      | dudu524      |
| \[問題\] 提摩出裝請益                               | 22      | e3890313     |
| \[閒聊\] LOL有像諸葛亮一樣的角色嗎?                 | 15      | BHAIRE       |
| \[揪團\] 銅二積分                                   | 1       | jojo0611188  |
| \[情報\] 測試服改動：麗珊卓延後改動，隨機峽谷登     | 38      | BRITAINCAT   |
| Re: \[閒聊\] 金銀銅以為鉑鑽比他們強多少             |         | fdfdfdfd51   |
| \[閒聊\] 小熊 Yuniko FB                             | 46      | d86249       |
| \[閒聊\] 隊伍開戰角太多怎麼辦？                     | 14      | ccyaztfe     |
| \[問題\] 一些達瑞斯的問題                           | 14      | andrew0312   |
| \[問題\] 各位會算哪時候會開嗎                       | 16      | a87308151    |
| \[問題\] 要怎麼樣才能把賈克斯玩得跟鬼一樣?          |         | Fantasyweed  |
| Re: \[閒聊\] 金銀銅以為鉑鑽比他們強多少             | 1       | rainyday1908 |
| \[實況\] FW NL / 煞氣o狂by衝崩銨                    | 52      | khuntoria    |
| (本文已被刪除) \[skyprotector\]                     |         | -            |
| Re: \[閒聊\] 丁特 FB                                | 7       | zonglunli    |
| \[問題\] 隊友不願意冒著敵人的砲火前進 怎麼辦??      | 7       | hochengyuan  |
| Re: \[閒聊\] 丁特 FB                                | X4      | machia       |
| Re: \[閒聊\] 丁特 FB                                | 2       | apostleship  |
| \[外絮\] EC Global Power Rankings (28/3)            | 37      | coolplus     |
| \[揪團\] 銅二積分 快速爬                            | 7       | WarmDude     |
| \[實況\]爆到生活無法自理 113電競主播                |         | andy1014     |
| \[閒聊\] 哪些狀況英雄會金金的                       | 14      | HAHEinthebar |
| \[外絮\] SSG Haru:擊敗SKT是因為三路對線全優勢       | 14      | s80554       |
| \[閒聊\] 大家來分享一下艾(ㄌ)可(G)寶袋吧            | 9       | TwinkyLee    |
| \[閒聊\] 這季閃電狼跟其他隊的差距                   | 51      | ss8901234    |
| Re: \[閒聊\] 丁特 FB                                | X2      | ardan3355    |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 3       | heybro       |
| (本文已被刪除) \[andy31313\]                        | 1       | -            |
| \[實況\] 改革家ForFun國動                           | 爆      | johnnywanwan |
| (本文已被刪除) \[pzboy\]                            |         | -            |
| \[揪團\] 彈性積分                                   |         | onlydoing    |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 21      | csgod1325    |
| \[閒聊\] 為什麼遲遲不開放用自己的照片當頭像         | 21      | waiting0212  |
| \[閒聊\] AHQ FB                                     | 22      | jackal44748  |
| \[情報\] 2017 LCK春季季後賽 賽程                    | 7       | dinter9921   |
| \[電競\] 2017 LCK Spring W10D1                      | 56      | cherrycheese |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 19      | heybro       |
| \[閒聊\] 丁特最近壓力是不是很大??                   | 23      | gofee        |
| \[心得\] 上路提摩-香菇農場                          | 9       | meat18ball   |
| \[電競\] LJL 春季升降賽 Day2                        | 3       | superRKO     |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 3       | zephyrhymn   |
| Re: \[閒聊\] 金銀銅以為鉑鑽比他們強多少             | 4       | bassmaster   |
| (已被rainnawind刪除) <ant2248673>D1                 | X1      | -            |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 21      | godshibainu  |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 6       | yjnfans      |
| \[問題\] 被隊友嘴扣大怎麼辦                         | 21      | c753968412   |
| \[揪團\] 無罪開心糾團-4                             | 2       | a15661263    |
| \[閒聊\] 英雄聯盟比賽的電競椅 乘坐的感覺是怎樣?     | 17      | vovzz        |
| Re: \[閒聊\] 這季閃電狼跟其他隊的差距               | 30      | bluejark     |
| \[閒聊\] 閃電狼世界冠軍路差多少                     | 18      | xbeyond      |
| Re: \[閒聊\] 閃電狼世界冠軍路差多少                 |         | xyyzzz       |
| Re: \[外絮\] EC Global Power Rankings (Reddit回應)  | 35      | yiwangneko   |
| \[問題\] 宏宏這麼敢點是不是因為沒有刺客給他壓力     | 48      | tommy123310  |
| \[閒聊\] 【滑對決】算吧！國中數學題大比拼           | 29      | tigerclamp   |
| \[外絮\] 宇宙戰隊太過美譽？KT三連敗狀態低迷         | 3       | zzsh3533     |
| \[實況\] 噯卑彌呼，爬韓服～                         | 1       | Destinyandy  |
| \[公告\] LoL 板 開始舉辦樂透!                       | 6       | rainnawind   |
| \[外絮\] 真的假的？Riot洩露下個史詩造型是凱特琳     | 15      | zzsh3533     |
| \[實況\] 叉燒/BD大平台                              | 3       | chi972121    |
| \[閒聊\] 隊友遇到偶像跑去送頭該怎辦                 |         | songgood     |
| \[問題\] 新版加里歐                                 | 3       | sinsandy     |
| Re: \[外絮\] 真的假的？Riot洩露下個史詩造型是凱特琳 | 32      | AlzioNever   |
| \[閒聊\] 現在飛斯的海神三叉戟到底算強還弱           | 13      | tom80727     |
| \[閒聊\] 華義SPIDER FB Rins的新歡                   | 1       | iamfenixsc   |
| \[實況\] 妳男友正在享受我 快樂視角                  |         | macassans    |
| \[閒聊\] 有人遇過什麼改革家什麼國動的嗎             |         | PUTAIR       |
| \[閒聊\] 非韓最強閃電狼排第六名？                   |         | zindqq       |
| \[閒聊\] 關於萊門寶典                               | 5       | GOBS         |
| \[閒聊\] 解說記得 微博                              |         | Comebuy      |
| \[閒聊\] 英雄名稱/PTT ID                            | 19      | Vladimir     |
| \[閒聊\] ahq Tiger Blue週記 2017 Spring 7           | 19      | rabbitball19 |
| Re: \[閒聊\] 丁特 FB                                | 爆      | blsy4300145  |
| \[閒聊\] 有一些喜歡詩詞id的朋友嗎                   | 22      | HydraQ       |
| \[閒聊\] 台服有人能劈死歐服嗎?                      | 6       | Godman0618   |
| \[實況\] 斗基督機大神 鬼話新聞紅蟻                  | 54      | dase1352     |
| Re: \[閒聊\] 丁特 FB                                | 32      | diefish5566  |
| \[閒聊\] 228戰隊如果可以跟HKE一戰的話大家支持?      | 18      | BHAIRE       |
| \[實況\] 獄胤天 自己的頻道圖自己畫，歡迎來玩!       |         | asdfg5247    |
| \[閒聊\] LMS是不是需要一個反派                      | 29      | ss8901234    |
| \[影片\] 韓服600分 西門塔隆示範最正確的入場時機     | 13      | powyo        |
| \[實況\] FW Winds ( 關 )                            | 20      | Greeyy       |
| \[揪團\] (滿)                                       | 1       | power5507    |
| \[閒聊\] 鍾老闆為何不讓toyz光榮退休?                |         | China666     |
| \[問題\] 為什麼天賦要點一點吸血?                    | 7       | ccrhalp      |
| \[閒聊\] 當今各路非韓最強是誰?                      |         | godsong5566  |
| \[問題\] 海鮮角是不是很難拿S+啊?                    | 9       | ru04ul4      |
| Re: \[閒聊\] 丁特 FB                                | 爆      | GOBS         |
| Re: \[閒聊\] 當今各路非韓最強是誰?                  | 5       | live147222   |
| \[閒聊\] 凱能上路                                   | 10      | SHORTRED     |
| (本文已被刪除) \[VVVV5555\]                         | 1       | -            |
| \[閒聊\] 現在丁特跟228約戰BO3的話 勝率有多少?       | 12      | vovzz        |
| (本文已被刪除) \[ashin0831\]                        |         | -            |
| \[閒聊\]隊友選辛吉德JG，不吃野斷各路兵線，有解嗎?   | 8       | ayjfi250     |
| \[閒聊\] 丁特會這麼黑 最大的原因                    |         | fantasy0937  |
| \[外絮\] 皇族 微博                                  | 17      | diefish5566  |
| Re: \[閒聊\] 丁特 FB                                | X2      | VVVV5555     |
| Re: \[實況\] 改革家ForFun國動                       | 71      | forng        |
| Re: \[閒聊\] 現在丁特跟228約戰BO3的話 勝率有多少?   | 6       | defendant    |

解釋爬蟲結果
------------

``` r
dim(LOL_dataframe)
```

    ## [1] 100   3

``` r
nrow(LOL_dataframe)
```

    ## [1] 100

``` r
str(LOL_dataframe)
```

    ## 'data.frame':    100 obs. of  3 variables:
    ##  $ title  : Factor w/ 85 levels "\n\t\t\t\n\t\t\t\t(本文已被刪除) [skyprotector]\n\t\t\t\n\t\t\t",..: 2 15 8 6 11 10 9 17 12 13 ...
    ##  $ PushNum: Factor w/ 40 levels "","1","14","15",..: 14 2 7 8 4 2 9 1 10 3 ...
    ##  $ Author : Factor w/ 88 levels "-","a87308151",..: 19 8 10 11 5 15 6 13 9 7 ...

共有3行，100列

``` r
table(LOL_dataframe[3])
```

    ## 
    ##            -    a87308151   andrew0312  apostleship       BHAIRE 
    ##            6            1            1            1            2 
    ##   BRITAINCAT     ccyaztfe      cha7919       d86249      dudu524 
    ##            1            1            1            1            1 
    ##     e3890313  Fantasyweed   fdfdfdfd51  hochengyuan  jojo0611188 
    ##            1            1            1            1            1 
    ##    khuntoria       machia rainyday1908      samhou6    zonglunli 
    ##            1            1            1            1            1 
    ##     andy1014    ardan3355 cherrycheese     coolplus    csgod1325 
    ##            1            1            1            1            1 
    ##   dinter9921        gofee HAHEinthebar       heybro  jackal44748 
    ##            1            1            1            2            1 
    ## johnnywanwan    onlydoing       s80554    ss8901234    TwinkyLee 
    ##            1            1            1            2            1 
    ##  waiting0212     WarmDude    a15661263   bassmaster     bluejark 
    ##            1            1            1            1            1 
    ##   c753968412  Destinyandy  godshibainu   meat18ball   rainnawind 
    ##            1            1            1            1            1 
    ##     superRKO   tigerclamp  tommy123310        vovzz      xbeyond 
    ##            1            1            1            2            1 
    ##       xyyzzz   yiwangneko      yjnfans   zephyrhymn     zzsh3533 
    ##            1            1            1            1            2 
    ##   AlzioNever    asdfg5247  blsy4300145    chi972121      Comebuy 
    ##            1            1            1            1            1 
    ##     dase1352  diefish5566         GOBS   Godman0618       HydraQ 
    ##            1            2            2            1            1 
    ##   iamfenixsc    macassans       PUTAIR rabbitball19     sinsandy 
    ##            1            1            1            1            1 
    ##     songgood     tom80727     Vladimir       zindqq     ayjfi250 
    ##            1            1            1            1            1 
    ##      ccrhalp     China666    defendant  fantasy0937        forng 
    ##            1            1            1            1            1 
    ##  godsong5566       Greeyy   live147222    power5507        powyo 
    ##            1            1            1            1            1 
    ##      ru04ul4     SHORTRED     VVVV5555 
    ##            1            1            1

``` r
??table()
```

    ## starting httpd help server ...

    ##  done

被刪文者最多文章。

PTT LOL版常常被刪文
