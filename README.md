# yabai_skhd
本身有雙螢幕(最近想要新增到第三個了...有點不夠用了)，都會將各個應用程式放在不同的虛擬視窗，這時候就要頻繁使用觸碰版來拖曳視窗，長期使用下來真的感到很不方便！
偶然間發現yabai這個視窗管理工具(Tiling Window Management)，使用下來感覺很不錯。  
打算長期使用，所以就開了一個Repo存放設定檔案，接著在不同電腦中只要clone下來之後用軟連結的方式，就可以直接開始使用了。

另外，已經預設透過brew安裝好yabai以及skhd了。如果還沒有安裝的需要先安裝好才執行接下來的內容。

有使用到hyper key，利用karabiner將capslock改為hyper key了，可以視情況調整skhd的設定。

在`karabiner`裡面也會有complex modification對應的json file。

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

# 其他設定
在使用yabai時可以選擇要不要關閉Mac內建的系統完整性保護(SIP)設定，來換取更多的設定彈性。  
但是因為希望可以不要變動太多，可以盡量採用較小的變動避免在版本更新等等時又要額外花時間解決衝突問題，所以Repo內的設定檔不需要關閉SIP。

雖然不用關閉SIP，在Mac上還是有許多建議的設定如下：
- 設定鍵盤指揮中心
   1. `系統設定>>鍵盤>>鍵盤快速鍵>>(左側選單)指揮中心>>(右方checkbox)指揮中心>>將切換至桌面1,2,3等等選項開啟`
   2.  如果沒有出現切換至桌面符號，可以先新增幾個虛擬桌面，再根據上方路徑開啟即可看到選單
   3.  接著我們就可以使用ctrl+1,2,3...切換各個螢幕
 
      
- 減少動態效果(將切換螢幕過程從左右滑動>>Fade in out)
   1. `系統設定>>輔助使用>>(右側)顯示器>>減少動態效果 on`
 
    
- 設定Dock指揮中心設定，路徑為`系統設定>>桌面與Dock>>指揮中心`，設定如下：
   1. **根據最近的使用情況自動重新排列空間 OFF** (重要!)
   2. 切換至應用程式時，切換至含有應用程式打開視窗的空間 ON
   3. **依據應用程式將視窗分組 OFF** (重要!)
   4. 顯示器有單獨空間 ON


--- 

# Karabiner Settings
Karabiner協助修改Mac鍵盤的映射，最常使用的功能如MacOS的hyperkey:cmd+option+ctrl+shift，我們可以透過將較少使用的capslock替換為同時按下這四個案件，來觸發hyper key。

```
{
    "description": "我的個人設定",
    "manipulators": [
        {
            "from": {
                "key_code": "h",
                "modifiers": {
                    "mandatory": [
                        "right_command"
                    ],
                    "optional": [
                        "any"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "left_arrow"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "j",
                "modifiers": {
                    "mandatory": [
                        "right_command"
                    ],
                    "optional": [
                        "any"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "down_arrow"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "k",
                "modifiers": {
                    "mandatory": [
                        "right_command"
                    ],
                    "optional": [
                        "any"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "up_arrow"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "l",
                "modifiers": {
                    "mandatory": [
                        "right_command"
                    ],
                    "optional": [
                        "any"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "right_arrow"
                }
            ],
            "type": "basic"
        },
        {
            "description": "Change caps_lock to command+control+option+shift.",
            "from": {
                "key_code": "caps_lock",
                "modifiers": {
                    "optional": [
                        "any"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "left_shift",
                    "modifiers": [
                        "left_command",
                        "left_control",
                        "left_option"
                    ]
                }
            ],
            "type": "basic"
        },
        {
            "description": "Hyper+H to Ctrl+Left",
            "from": {
                "key_code": "h",
                "modifiers": {
                    "mandatory": [
                        "left_shift",
                        "left_command",
                        "left_control",
                        "left_option"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "left_arrow",
                    "modifiers": [
                        "left_control"
                    ]
                }
            ],
            "type": "basic"
        },
        {
            "description": "Hyper+L to Ctrl+Left",
            "from": {
                "key_code": "l",
                "modifiers": {
                    "mandatory": [
                        "left_shift",
                        "left_command",
                        "left_control",
                        "left_option"
                    ]
                }
            },
            "to": [
                {
                    "key_code": "right_arrow",
                    "modifiers": [
                        "left_control"
                    ]
                }
            ],
            "type": "basic"
        }
    ]
}
```