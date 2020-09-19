# CCNA_OSPF
開放最快路徑第一

# 應用情境

如果說網管們在設計網路架構時，靜態路由 > 動態路由，真要用到動態路由，則觀看公司規模，
如果是小型企業，大多使用動態路由中的 RIP 路由協定，倘若規模稍大為中大型企業，
則動態路由會建議使用 OSPF 開放最短路徑優先的路由協定。

# IGP & EIGP

IGP 為 Interil Gateway Protocol, 與 EIGP (Enhanced Interior GW Protocol) 相互應。
而 OSOF 算是 IGP 中比較常見的動態路由協定。

# 路徑演算法

動態路由協定中常見的 RIP 與 OSPF 就是分別使用不同的演算法，前者屬於計算 hop count 的 distance vector，
而後者屬於觀察 Link State 鏈結狀態，兩者不同，一個是基於實體路徑 hop 數量，另一個是基於 cost 傳輸質量。

# LSDB 資料表紀錄

類似資料庫，同一區域的路由器的資料表都會是一樣的。

# LSDB 資料表更新

採用 Link State Update 鏈結狀態更新，使用 Multicast 224.0.0.5 和 224.0.0.6 來傳送資料表更新訊息。

# IP port

OSPF 與其他動態路由協定不同的是，它不經由 TCP、UDP，僅使用 IP 層，IP port 是 89。

# Backbone 骨幹區域與骨幹路由器

即兩個非骨幹區域邏輯性地相互連接的區域。
骨幹區域負責分配路由資訊給非骨幹路由。

![backbone area](https://raw.githubusercontent.com/QueenieCplusplus/CCNA2020_OSPF/master/backbone_area.png)


R2 & R3 兩路由器均開啟了 OSPF，所以為骨幹路由器。

R2 & R3 兩路由器也有端口開啟了 AS 內的鏈路狀態路由表的更新監聽，所以也為自治區邊界路由器 ASBR。

R1 & R5 只需要維護該區域 Area1 的 LSDB (包含紀錄拓樸狀態的變化、包含 LSA 的 flood)。

R3 & R4 只需要維護該區域 Area2 的 LSDB (包含紀錄拓樸狀態的變化、包含 LSA 的 flood)。

Area 0 IP 為 0.0.0.0，使兩個以上不同的區域彼此間能展開訊息交流。

# Stub 末梢區域

設定一預設路由，控管區域內外進出的路由資訊，避免區域外部資訊對區域內部進行泛洪。

(尚區分為完全末梢、不完全末梢)



