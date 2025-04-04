#自用 Loon 懒人规则，无重写和脚本。
#Date: 2025.04.02
#Author: Loon

[General]
ip-mode = v4-only
ipv6 = false
skip-proxy = 192.168.0.0/16,10.0.0.0/8,172.16.0.0/12,localhost,*.local,e.crashlynatics.com
bypass-tun = 10.0.0.0/8,100.64.0.0/10,127.0.0.0/8,169.254.0.0/16,172.16.0.0/12,192.0.0.0/24,192.0.2.0/24,192.88.99.0/24,192.168.0.0/16,198.51.100.0/24,203.0.113.0/24,224.0.0.0/4,255.255.255.255/32
dns-server = system,119.29.29.29,114.114.114.114,223.5.5.5
allow-wifi-access = false
wifi-access-http-port = 7222
wifi-access-socks5-port = 7221
proxy-test-url = http://cp.cloudflare.com/generate_204
internet-test-url = http://wifi.vivo.com.cn/generate_204
test-timeout = 3
interface-mode = auto

[Proxy]

[Remote Proxy]
# 演示用的无效订阅链接，可删除。
AMY = https://airportsub.com/purchasing-subscribe/,udp=true,fast-open=default,vmess-aead=true,skip-cert-verify=true,enabled=true,flexible-sni=true,img-url=https://raw.githubusercontent.com/Orz-3/mini/master/Color/Amy.png
Boslife = https://airportsub.com/purchasing-subscribe/,udp=true,fast-open=default,vmess-aead=true,skip-cert-verify=true,enabled=true,flexible-sni=true,img-url=https://raw.githubusercontent.com/Orz-3/mini/master/Color/Boslife.png

[Proxy Chain]

[Proxy Group]
Available = select,HK_Filter,TW_Filter,JP_Filter,KR_Filter,US_Filter,SG_Filter,HK,TW,SG,JP,KR,US,url = http://cp.cloudflare.com/generate_204,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Available.png
YouTube = select,Available,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/YouTube.png
Telegram = select,Available,TW,HK,SG,JP,KR,US,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Telegram.png
ChatGPT = select,Available,SG,US,JP,KR,TW,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/ChatGPT.png
Gemini = select,Available,SG,US,JP,KR,TW,img-url = https://raw.githubusercontent.com/lige47/QuanX-icon-rule/main/icon/gemini.png
HK = select,HK_Filter,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Hong_Kong.png
TW = select,TW_Filter,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Taiwan.png
SG = select,SG_Filter,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Singapore.png
JP = select,JP_Filter,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Japan.png
KR = select,KR_Filter,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Korea.png
US = select,US_Filter,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/United_States.png

[Remote Filter]
HK_Filter = NameRegex, FilterKey = "(?i)(港|HK|Hong)"
TW_Filter = NameRegex, FilterKey = "(?i)(台|TW|Tai)"
JP_Filter = NameRegex, FilterKey = "(?i)(日本|川日|东京|大阪|泉日|埼玉|沪日|深日|JP|Japan)"
KR_Filter = NameRegex, FilterKey = "(?i)(KR|Korea|KOR|首尔|韩|韓)"
US_Filter = NameRegex, FilterKey = "(?i)(美|波特兰|达拉斯|俄勒冈|凤凰城|费利蒙|硅谷|拉斯维加斯|洛杉矶|圣何塞|圣克拉拉|西雅图|芝加哥|US|United States)"
SG_Filter = NameRegex, FilterKey = "(?i)(新加坡|坡|狮城|SG|Singapore)"

[Rule]
#Type:DOMAIN-SUFFIX,DOMAIN,DOMAIN-KEYWORD,USER-AGENT,URL-REGEX,IP-CIDR
#Strategy:DIRECT,PROXY,REJECT
#Options:no-resolve(only for IP-CIDR,IP-CIDR2,GEOIP,IP-ASN)

GEOIP,cn,DIRECT
FINAL,Available

[Remote Rule]
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Loon/China/China_Domain.list, policy=DIRECT, tag=China Domain, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/China/China.list, policy=DIRECT, tag=China, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Gemini/Gemini.list, policy=Available, tag=Gemini, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Loon/Apple/Apple_Domain.list, policy=DIRECT, tag=Apple_Domain, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Apple/Apple.list, policy=DIRECT, tag=Apple, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Shadowrocket/OpenAI/OpenAI.list, policy=Available, tag=OpenAI, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/YouTube/YouTube.list, policy=YouTube, tag=YouTube, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Telegram/Telegram.list, policy=Telegram, tag=Telegram, enabled=true
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Proxy/Proxy.list, policy=Available, tag=Global, enabled=true

[Rewrite]

[Script]

[Plugin]
# 拓扑检测插件，默认未开启。
https://raw.githubusercontent.com/lige47/QuanX-icon-rule/main/scripts/wangluoxinxi.plugin, tag=拓扑检测, enabled=false
[Mitm]
skip-server-cert-verify = false
