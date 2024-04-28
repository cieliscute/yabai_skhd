# yabai_skhd
本身有雙螢幕(最近想要新增到第三個了...有點不夠用了)，都會將各個應用程式放在不同的虛擬視窗，這時候就要頻繁使用觸碰版來拖曳視窗，長期使用下來真的感到很不方便！
偶然間發現yabai這個視窗管理工具(Tiling Window Management)，使用下來感覺很不錯。  
打算長期使用，所以就開了一個Repo存放設定檔案，接著在不同電腦中只要clone下來之後用軟連結的方式，就可以直接開始使用了。

並且為了避免各個軟體中間的互相依賴，並沒有另外使用**Karabiner**等等的軟體來輔助hyper key  
所以在skhd內的設定不會包含hyper key

另外，已經預設透過brew安裝好yabai以及skhd了。如果還沒有安裝的需要先安裝好才執行接下來的內容。

# 使用步驟
1. 先進到`.config`位置 
```shell
cd ~/.config
```
> 如果不想存放在`.config`中也可以，但是有一些link就需要自行替換掉路徑
2. 將專案Clone下來
```shell
git clone https://github.com/cieliscute/yabai_skhd.git
```
2. 將Clone下來的Repo內的`yabairc`以及`skhdrc`軟連結到使用者根目錄下
```shell
ln -s ~/.config/yabai_skhd/yabairc ~/.yabairc
ln -s ~/.config/yabai_skhd/skhdrc ~/.skhdrc
```
> 如果路徑不同要自己修正

4. 執行skhd
```shell
skhd --start-service
```

執行到此階段之後，就可以將終端機給關閉了。後續會利用skhd內映射的快捷鍵啟用yabai功能。

5.啟用yabai
直接在鍵盤上按下`cmd+option+control+s` 啟用yabai (設定位於skhdrc內)

--- 

如果需要關閉yabai可以按下`cmd+option+control+q`  
當完全不需使用skhd時，則需要再開啟終端機輸入`skhd --stop-service`
