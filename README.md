# device-detector-js

Device-detector-js is a precise user agent parser and device detector written in TypeScript, backed by the largest and most up-to-date open-source user agent database.

Device-detector-js will parse any user agent and detect the browser, operating system, device used (desktop, tablet, mobile, tv, cars, console, etc.), brand and model. Works with Node.js and in the browser.

This library is heavily tested and relies on over 10,000 tests to detect thousands of user agent strings, even from rare and obscure browsers and devices.

#### This is a javascript port of [Matomo device-detector](https://github.com/matomo-org/device-detector) (4.1.0).

[![Coveralls github](https://img.shields.io/coveralls/github/etienne-martin/device-detector-js.svg)](https://coveralls.io/github/etienne-martin/device-detector-js)
[![CircleCI build](https://img.shields.io/circleci/project/github/RedSparr0w/node-csgo-parser.svg)](https://circleci.com/gh/etienne-martin/device-detector-js)
[![node version](https://img.shields.io/node/v/device-detector-js.svg)](https://www.npmjs.com/package/device-detector-js)
[![npm version](https://img.shields.io/npm/v/device-detector-js.svg)](https://www.npmjs.com/package/device-detector-js)
[![npm monthly downloads](https://img.shields.io/npm/dm/device-detector-js.svg)](https://www.npmjs.com/package/device-detector-js)

## Features

- No dependencies
- TypeScript support
- Thoroughly tested

## Demo

https://lx3rzx16x9.codesandbox.io/

## Getting Started

### Installation

To use device-detector-js in your project, run:

```bash
npm install device-detector-js
```

### Usage

##### ES2015 import:
```javascript
import DeviceDetector from "device-detector-js";
```

##### TypeScript import:
```typescript
import DeviceDetector = require("device-detector-js");
```

**Example** - user agent detection:

```javascript
import DeviceDetector from "device-detector-js";

const deviceDetector = new DeviceDetector();
const userAgent = "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.81 Safari/537.36";
const device = deviceDetector.parse(userAgent);

console.log(device);
```

Output:

```json
{
  "client": {
    "type": "browser",
    "name": "Chrome",
    "version": "69.0",
    "engine": "Blink",
    "engineVersion": ""
  },
  "os": {
    "name": "Mac",
    "version": "10.13",
    "platform": ""
  },
  "device": {
    "type": "desktop",
    "brand": "Apple",
    "model": ""
  },
  "bot": null
}
```

**Example** - bot detection:

```javascript
import BotDetector from "device-detector-js/dist/parsers/bot";

const botDetector = new BotDetector();
const userAgent = "Mozilla/5.0 (iPhone; CPU iPhone OS 6_0 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/6.0 Mobile/10A5376e Safari/8536.25 (compatible; Googlebot-Mobile/2.1; +http://www.google.com/bot.html)";
const bot = botDetector.parse(userAgent);

if (bot) {
  console.log(bot);
}
```

Output:

```json
{
  "name": "Googlebot",
  "category": "Search bot",
  "url": "http://www.google.com/bot.html",
  "producer": {
    "name": "Google Inc.",
    "url": "http://www.google.com"
  }
}
```

## API Documentation

#### new DeviceDetector([options])

- `options` <[Object]> Options object which might have the following properties:
  - `skipBotDetection` <[boolean]> If true, bot detection will completely be skipped (bots will be detected as regular devices). Defaults to `false`.
  - `versionTruncation` <[0 | 1 | 2 | 3 | null]> Passing `null` disables version truncation, so full versions will be returned. Defaults to `1`, only minor versions will be returned (e.g. X.Y).
  
## TypeScript

Type definitions are included in this library and exposed via:

```typescript
import { DeviceDetectorResult, DeviceDetectorOptions } from "device-detector-js";
``` 

## ⚠️ Browser Environment

Even though this library can run in the browser, **it is strongly advised against doing so**, unless you are not concerned with performance. Keep in mind that using this library in browser-side code means sending around 432 KB of Regex rules and 144 KB of javascript (uncompressed and unminified), which may result in a poor user experience for people with a slow Internet connection.

**You may experience inconsistencies when running this library in a browser environment, as some browsers like Safari do not yet support lookbehind syntax.**
  
## What device-detector-js is able to detect

The lists below are auto generated and updated from time to time. Some of them might not be complete.
*Last update: 2021/01/08*

### List of detected operating systems:

AIX, Android, AmigaOS, Apple TV, Arch Linux, BackTrack, Bada, BeOS, BlackBerry OS, BlackBerry Tablet OS, Brew, CentOS, Chrome OS, CyanogenMod, Debian, Deepin, DragonFly, Fedora, Firefox OS, Fire OS, Freebox, FreeBSD, FydeOS, Gentoo, Google TV, HP-UX, Haiku OS, IRIX, Inferno, KaiOS, Knoppix, Kubuntu, GNU/Linux, Lubuntu, VectorLinux, Mac, Maemo, Mandriva, MeeGo, MocorDroid, Mint, MildWild, MorphOS, NetBSD, MTK / Nucleus, MRE, Nintendo, Nintendo Mobile, OS/2, OSF1, OpenBSD, Ordissimo, PlayStation Portable, PlayStation, Red Hat, RISC OS, Rosa, Remix OS, RazoDroiD, Sabayon, SUSE, Sailfish OS, SeewoOS, Slackware, Solaris, Syllable, Symbian, Symbian OS, Symbian OS Series 40, Symbian OS Series 60, Symbian^3, ThreadX, Tizen, TmaxOS, Ubuntu, watchOS, WebTV, Whale OS, Windows, Windows CE, Windows IoT, Windows Mobile, Windows Phone, Windows RT, Xbox, Xubuntu, YunOs, iOS, palmOS, webOS

### List of detected browsers:

115 Browser, 2345 Browser, 360 Phone Browser, 360 Browser, Avant Browser, ABrowse, ANT Fresco, ANTGalio, Aloha Browser, Aloha Browser Lite, Amaya, Amigo, Android Browser, AOL Desktop, AOL Shield, Arora, Arctic Fox, Amiga Voyager, Amiga Aweb, Atom, Atomic Web Browser, Avast Secure Browser, AVG Secure Browser, Beaker Browser, Beamrise, BlackBerry Browser, Baidu Browser, Baidu Spark, Basilisk, Beonex, BlackHawk, Bunjalloo, B-Line, Blue Browser, Borealis Navigator, Brave, BriskBard, BrowseX, Browzar, Camino, CCleaner, Centaury, Coc Coc, Colibri, Comodo Dragon, Coast, Charon, CM Browser, Chrome Frame, Headless Chrome, Chrome, Chrome Mobile iOS, Conkeror, Chrome Mobile, CoolNovo, CometBird, COS Browser, Chim Lac, ChromePlus, Chromium, Cyberfox, Cheshire, Crusta, Crazy Browser, Cunaguaro, Chrome Webview, dbrowser, Deepnet Explorer, Delta Browser, Dolphin, Dorado, Dooble, Dillo, DuckDuckGo Privacy Browser, Ecosia, Epic, Elinks, Element Browser, Elements Browser, eZ Browser, EUI Browser, GNOME Web, Espial TV Browser, Falkon, Faux Browser, Firefox Mobile iOS, Firebird, Fluid, Fennec, Firefox, Firefox Focus, Firefox Reality, Firefox Rocket, Flock, Firefox Mobile, Fireweb, Fireweb Navigator, FreeU, Galeon, Ghostery Privacy Browser, Glass Browser, Google Earth, GOG Galaxy, Hawk Turbo Browser, hola! Browser, HotJava, Huawei Browser, IBrowse, iCab, iCab Mobile, Iridium, Iron Mobile, IceCat, IceDragon, Isivioo, Iceweasel, Internet Explorer, IE Mobile, Iron, Japan Browser, Jasmine, Jig Browser, Jig Browser Plus, Jio Browser, K.Browser, Kindle Browser, K-meleon, Konqueror, Kapiko, Kinza, Kiwi, Kode Browser, Kylo, Kazehakase, Cheetah Browser, LieBaoFast, LG Browser, Light, Links, Lovense Browser, LuaKit, Lulumi, Lunascape, Lunascape Lite, Lynx, mCent, MicroB, NCSA Mosaic, Meizu Browser, Mercury, Mobile Safari, Midori, Mobicip, MIUI Browser, Mobile Silk, Minimo, Mint Browser, Maxthon, MxNitro, Mypal, Monument Browser, MAUI WAP Browser, Navigateur Web, NFS Browser, Nokia Browser, Nokia OSS Browser, Nokia Ovi Browser, Nox Browser, NetSurf, NetFront, NetFront Life, NetPositive, Netscape, NTENT Browser, Oculus Browser, Opera Mini iOS, Obigo, Odin, Odyssey Web Browser, Off By One, OhHai Browser, ONE Browser, Opera GX, Opera Neon, Opera Devices, Opera Mini, Opera Mobile, Opera, Opera Next, Opera Touch, Ordissimo, Oregano, Origin In-Game Overlay, Origyn Web Browser, Openwave Mobile Browser, OmniWeb, Otter Browser, Palm Blazer, Pale Moon, Polypane, Oppo Browser, Palm Pre, Puffin, Palm WebPro, Palmscape, Phoenix, Phoenix Browser, PlayFree Browser, Polaris, Polarity, PrivacyWall, Microsoft Edge, QQ Browser Mini, QQ Browser, Qutebrowser, Quark, QupZilla, Qwant Mobile, QtWebEngine, Realme Browser, Rekonq, RockMelt, Samsung Browser, Sailfish Browser, Seewo Browser, SEMC-Browser, Sogou Explorer, Safari, Safe Exam Browser, SalamWeb, SFive, Shiira, SimpleBrowser, Sizzy, Skyfire, Seraphic Sraf, Sleipnir, Slimjet, 7Star, Smart Lenovo Browser, Snowshoe, Sogou Mobile Browser, Splash, Sputnik Browser, Sunrise, SuperBird, Super Fast Browser, surf, Stargon, START Internet Browser, Steam In-Game Overlay, Streamy, Swiftfox, Seznam Browser, T-Browser, t-online.de Browser, Tao Browser, TenFourFox, Tenta Browser, Tizen Browser, Tungsten, ToGate, TweakStyle, TV Bro, UBrowser, UC Browser, UC Browser Mini, UC Browser Turbo, UR Browser, Uzbl, Vivaldi, vivo Browser, Vision Mobile Browser, VMware AirWatch, Wear Internet Browser, Web Explorer, WebPositive, Waterfox, Whale Browser, wOSBrowser, WeTab Browser, Yahoo! Japan Browser, Yandex Browser, Yandex Browser Lite, Yaani Browser, Yolo Browser, Xiino, Xvast, Zvu

### List of detected browser engines:

WebKit, Blink, Trident, Text-based, Dillo, iCab, Elektra, Presto, Gecko, KHTML, NetFront, Edge, NetSurf, Servo, Goanna

### List of detected libraries:

aiohttp, curl, Faraday, Go-http-client, Google HTTP Java Client, Guzzle (PHP HTTP Client), HTTPie, HTTP_Request2, Java, libdnf, Mechanize, Node Fetch, OkHttp, Perl, Perl REST::Client, Postman Desktop, Python Requests, Python urllib, ReactorNetty, REST Client for Ruby, RestSharp, ScalaJ HTTP, urlgrabber (yum), Wget, WWW-Mechanize

### List of detected media players:

Audacious, Banshee, Boxee, Clementine, Deezer, FlyCast, Foobar2000, Google Podcasts, iTunes, Kodi, MediaMonkey, Miro, mpv, Music Player Daemon, NexPlayer, Nightingale, QuickTime, Songbird, Stagefright, SubStream, VLC, Winamp, Windows Media Player, XBMC

### List of detected mobile apps:

AndroidDownloadManager, AntennaPod, Apple News, Baidu Box App, BeyondPod, BingWebApp, bPod, CastBox, Castro, Castro 2, CrosswalkApp, DingTalk, DoggCatcher, douban App, Facebook, Facebook Messenger, FeedR, Flipboard App, Google Go, Google Play Newsstand, Google Plus, Google Search App, HeyTapBrowser, iCatcher, Instacast, Instagram App, Instapaper, Keeper Password Manager, Kik, Line, LinkedIn, NewsArticle App, Overcast, Pinterest, Player FM, Pocket Casts, Podcast & Radio Addict, Podcast Republic, Podcasts, Podcat, Podcatcher Deluxe, Podkicker, Roblox, RSSRadio, Sina Weibo, Siri, Skyeng Teachers, Snapchat, SogouSearch App, tieba, TopBuzz, Twitter, U-Cursos, UnityPlayer, Viber, WeChat, WeChat Share Extension, WhatsApp, Yahoo! Japan, Yelp Mobile, YouTube and *mobile apps using [AFNetworking](https://github.com/AFNetworking/AFNetworking)*

### List of detected PIMs (personal information manager):

Airmail, Barca, DAVdroid, Lotus Notes, MailBar, Microsoft Outlook, Outlook Express, Postbox, SeaMonkey, The Bat!, Thunderbird

### List of detected feed readers:

Akregator, Apple PubSub, BashPodder, Breaker, Downcast, FeedDemon, Feeddler RSS Reader, gPodder, JetBrains Omea Reader, Liferea, NetNewsWire, Newsbeuter, NewsBlur, NewsBlur Mobile App, PritTorrent, Pulp, QuiteRSS, ReadKit, Reeder, RSS Bandit, RSS Junkie, RSSOwl, Stringer

### List of brands with detected devices:

2E, 3Q, 4Good, 4ife, 360, 8848, A1, Accent, Ace, Acer, Advan, Advance, AGM, Ainol, Airness, Airties, AIS, Aiwa, Akai, Alba, Alcatel, Alcor, ALDI SÜD, Alfawise, Aligator, AllCall, AllDocube, Allview, Allwinner, Altech UEC, Altice, altron, Amazon, AMGOO, Amigoo, Amoi, Andowl, Anry, ANS, Aoson, Apple, Archos, Arian Space, Ark, ArmPhone, Arnova, ARRIS, Artel, Artizlee, Asano, Asanzo, Ask, Assistant, Asus, AT&T, Atom, Audiovox, Avenzo, AVH, Avvio, Axxion, Azumi Mobile, BangOlufsen, Barnes & Noble, BBK, BB Mobile, BDF, Becker, Beeline, Beelink, Beetel, BenQ, BenQ-Siemens, Bezkam, BGH, Bigben, BIHEE, Billion, BioRugged, Bird, Bitel, Bitmore, Bkav, Black Bear, Black Fox, Blackview, Blaupunkt, Blu, Bluboo, Bluedot, Bluegood, Bluewave, Bmobile, Bobarry, bogo, Boway, bq, Brandt, Bravis, Brondi, Bush, CAGI, Capitel, Captiva, Carrefour, Casio, Casper, Cat, Celcus, Celkon, Changhong, Cherry Mobile, China Mobile, Chuwi, Clarmin, Cloudfone, Cloudpad, Clout, CnM, Coby Kyros, Comio, Compal, Compaq, ComTrade Tesla, Concord, ConCorde, Condor, Conquest, Contixo, Coolpad, Cowon, CreNova, Crescent, Cricket, Crius Mea, Crony, Crosscall, Cube, CUBOT, CVTE, Cyrus, Daewoo, Danew, Datang, Datawind, Datsun, Dbtel, Dell, Denver, Desay, DeWalt, DEXP, Dialog, Dicam, Digi, Digicel, Digihome, Digiland, Digma, Diva, Divisat, DMM, DNS, DoCoMo, Doffler, Dolamee, Doogee, Doopro, Doov, Dopod, Doro, Droxio, Dune HD, E-Boda, E-Ceros, E-tel, Easypix, EBEST, Echo Mobiles, ECS, EE, EKO, Eks Mobility, ELARI, Element, Elenberg, Elephone, Eltex, Energizer, Energy Sistem, Enot, Epik One, Ergo, Ericsson, Ericy, Essential, Essentielb, eSTAR, Eton, eTouch, Etuline, Eurostar, Evercoss, Evertek, Evolio, Evolveo, EvroMedia, ExMobile, EXO, Explay, Extrem, Ezio, Ezze, Fairphone, Famoco, FarEasTone, Fengxiang, Fero, FiGO, FinePower, Finlux, FireFly Mobile, Fly, FNB, Fondi, Fonos, FORME, Forstar, Fortis, Foxconn, Freetel, Fujitsu, G-TiDE, Garmin-Asus, Gateway, Gemini, General Mobile, GEOFOX, Geotel, Ghia, Ghong, Gigabyte, Gigaset, Ginzzu, Gionee, Globex, GOCLEVER, Goly, Gome, GoMobile, Google, Goophone, Gradiente, Grape, Gree, Grundig, Hafury, Haier, HannSpree, Hardkernel, Hasee, Helio, Hezire, Hi-Level, Highscreen, Hipstreet, Hisense, Hitachi, Hoffmann, Hometech, Homtom, Hoozo, Hosin, Hotel, Hotwav, How, HP, HTC, Huadoo, Huawei, Humax, Hurricane, Hyrican, Hyundai, i-Cherry, i-Joy, i-mate, i-mobile, iBall, iBerry, iBrit, IconBIT, iDroid, iGet, iHunt, Ikea, iKoMo, iLA, iLife, iMars, IMO Mobile, Impression, Inco, iNew, Infinix, InFocus, Inkti, InnJoo, Innostream, Inoi, INQ, Insignia, Intek, Intex, Inverto, Invin, iOcean, iPro, IQM, Irbis, Iris, iRola, iRulu, iSWAG, iTel, iTruck, iVA, iView, iVooMi, iZotron, JAY-Tech, JFone, Jiayu, Jinga, JKL, Jolla, Just5, JVC, K-Touch, Kaan, Kaiomy, Kalley, Kanji, Karbonn, KATV1, Kazam, KDDI, Kempler & Strauss, Keneksi, Kenxinda, Kiano, Kingsun, Kivi, Klipad, Kocaso, Kodak, Kogan, Komu, Konka, Konrow, Koobee, Koolnee, Kooper, KOPO, Koridy, KRONO, Krüger&Matz, KT-Tech, Kuliao, Kult, Kumai, Kyocera, Kzen, LAIQ, Land Rover, Landvo, Lanix, Lark, Lava, LCT, Leagoo, Ledstar, LeEco, Leff, Lemhoov, Lenco, Lenovo, Leotec, Le Pan, Lephone, Lesia, Lexand, Lexibook, LG, Lingwin, Linsar, Loewe, Logic, Logicom, Lumigon, Lumus, Luna, Luxor, LYF, M.T.T., M4tel, Macoox, Majestic, Mann, Manta Multimedia, Masstel, Matrix, Maxcom, Maxtron, MAXVI, Maxwest, Maze, meanIT, Mecer, Mecool, Mediacom, MediaTek, Medion, MEEG, MegaFon, Meitu, Meizu, Melrose, Memup, Metz, MEU, MicroMax, Microsoft, Minix, Mintt, Mio, Miray, Mito, Mitsubishi, MIXC, MiXzo, MLLED, MLS, Mobicel, Mobiistar, Mobiola, Mobistel, MobiWire, Mobo, Modecom, Mofut, Motorola, Movic, Mpman, MSI, MTC, MTN, Multilaser, MYFON, MyPhone, Myria, Mystery, MyTab, MyWigo, National, Navitech, Navon, NEC, Neffos, Neomi, Netgear, NeuImage, Newgen, Newland, Newman, NewsMy, NEXBOX, Nexian, NEXON, Nextbit, NextBook, NextTab, NGM, NG Optics, Nikon, Nintendo, NOA, Noain, Nobby, Noblex, Nokia, Nomi, Nomu, Nordmende, NorthTech, Nos, Nous, NuAns, NUU Mobile, Nuvo, Nvidia, NYX Mobile, O+, O2, Oale, Obi, Odys, Okapia, Onda, OnePlus, Onix, ONN, OpelMobile, Openbox, OPPO, Opsson, Orange, Orbic, Ordissimo, Ouki, Oukitel, OUYA, Overmax, Ovvi, Owwo, Oysters, Oyyu, OzoneHD, P-UP, Palm, Panacom, Panasonic, Pantech, PCBOX, PCD, PCD Argentina, PEAQ, Pentagram, Phicomm, Philco, Philips, Phonemax, phoneOne, Pioneer, Pixelphone, Pixus, Planet Computers, Ployer, Plum, PocketBook, POCO, Point of View, Polaroid, PolyPad, Polytron, Pomp, Poppox, Positivo, Positivo BGH, PPTV, Premio, Prestigio, Primepad, Primux, Prixton, Proline, ProScan, Protruly, PULID, Q-Touch, Q.Bell, Qilive, QMobile, Qtek, Quantum, Quechua, Qumo, R-TV, Ramos, Ravoz, Razer, RCA Tablets, Reach, Readboy, Realme, RED, Reeder, Rikomagic, RIM, Rinno, Ritmix, Ritzviva, Riviera, Roadrover, Rokit, Roku, Rombica, Ross&Moor, Rover, RoverPad, RT Project, RugGear, Runbo, Ryte, Safaricom, Sagem, Salora, Samsung, Sanei, Sansui, Santin, Sanyo, Savio, Schneider, Sega, Selenga, Selevision, Selfix, SEMP TCL, Sencor, Sendo, Senkatel, Senseit, Senwa, SFR, Sharp, Shift Phones, Shtrikh-M, Shuttle, Sico, Siemens, Sigma, Silelis, Silent Circle, Simbans, Siragon, Sky, Skyworth, Smadl, Smailo, Smart, SMARTEC, Smartfren, Smartisan, Softbank, Solone, Sonim, Sony, Sony Ericsson, Soundmax, Soyes, SPC, Spectrum, Spice, SQOOL, Star, Starlight, Starmobile, Starway, STF Mobile, STK, Stonex, Storex, Sugar, Sumvision, Sunstech, SunVan, Sunvell, SuperSonic, Supra, Swipe, SWISSMOBILITY, Swisstone, Symphony, Syrox, T-Mobile, Takara, Tanix, TB Touch, TCL, TD Systems, TechniSat, TechnoTrend, TechPad, Techwood, Teclast, Tecno Mobile, Tele2, Telefunken, Telego, Telenor, Telit, Tesco, Tesla, Tetratab, teXet, ThL, Thomson, Thuraya, TIANYU, Time2, Timovi, Tinai, Tinmo, TiPhone, Tolino, Tone, Tooky, Top House, Toplux, Torex, Toshiba, Touchmate, Transpeed, TrekStor, Trevi, Trifone, Tronsmart, True, TTEC, Tunisie Telecom, Turbo, Turbo-X, TurboKids, TVC, TWM, Twoe, Tymes, U.S. Cellular, Ugoos, Uhans, Uhappy, Ulefone, Umax, UMIDIGI, Unihertz, Unimax, Uniscope, UNIWA, Unknown, Unnecto, Unonu, Unowhy, UTOK, UTStarcom, VAIO, Vastking, Venso, Verico, Verizon, Vernee, Vertex, Vertu, Verykool, Vesta, Vestel, VGO TEL, Videocon, Videoweb, ViewSonic, Vinga, Vinsoc, Vipro, Vitelcom, Viumee, Vivax, Vivo, Vizio, VK Mobile, VKworld, Vodacom, Vodafone, Vonino, Vontar, Vorago, Vorke, Voto, Voxtel, Voyo, Vsmart, Vsun, Vulcan, VVETIME, Walton, Web TV, Weimei, WellcoM, Westpoint, Wexler, Wieppo, Wigor, Wiko, Wileyfox, Winds, Wink, Winmax, Wiseasy, Wizz, Wolder, Wolfgang, Wonu, Woo, Wortmann, Woxter, X-BO, X-TIGI, X-View, X.Vision, Xgody, Xiaolajiao, Xiaomi, Xion, Xolo, Xoro, Xshitou, Xtouch, Yandex, Yarvik, Yes, Yezz, Yoka TV, Yota, Ytone, Yu, Yuandao, Yusun, Yxtel, Zatec, Zebra, Zeemi, Zen, Zenek, Zentality, Zfiner, Zidoo, Ziox, Zonda, Zopo, ZTE, Zuum, Zync, ZYQ, öwn

### List of detected bots:

360Spider, Aboundexbot, Acoon, Adbeat, AddThis.com, ADMantX, ADmantX Service Fetcher, aHrefs Bot, Alexa Crawler, Alexa Site Audit, Amazon Route53 Health Check, Amorank Spider, Analytics SEO Crawler, ApacheBench, Applebot, Arachni, archive.org bot, Ask Jeeves, AspiegelBot, Awario, Awario, Backlink-Check.de, BacklinkCrawler, Baidu Spider, Barkrowler, BazQux Reader, BDCbot, BingBot, BitlyBot, Blekkobot, BLEXBot Crawler, Bloglovin, Blogtrottr, BoardReader, BoardReader Blog Indexer, Bountii Bot, BrandVerity, Browsershots, BUbiNG, Buck, BuiltWith, Butterfly Robot, Bytespider, CareerBot, Castro 2, Catchpoint, CATExplorador, ccBot crawler, Charlotte, Cliqzbot, CloudFlare Always Online, CloudFlare AMP Fetcher, Cloudflare Diagnostics, Collectd, CommaFeed, ContentKing, CSS Certificate Spider, Cốc Cốc Bot, Datadog Agent, Datanyze, Dataprovider, Daum, Dazoobot, Discobot, Domain Re-Animator Bot, Domains Project, DotBot, DuckDuckGo Bot, Easou Spider, eCairn-Grabber, EMail Exractor, EmailWolf, Embedly, evc-batch, ExaBot, ExactSeek Crawler, Ezooms, eZ Publish Link Validator, Facebook External Hit, Feedbin, FeedBurner, Feedly, Feedspot, Feed Wrangler, Fever, Findxbot, Flipboard, FreshRSS, Generic Bot, Generic Bot, Genieo Web filter, Gigablast, Gigabot, Gluten Free Crawler, Gmail Image Proxy, Goo, Googlebot, Google Cloud Scheduler, Google Favicon, Google PageSpeed Insights, Google Partner Monitoring, Google Search Console, Google Stackdriver Monitoring, Google Structured Data Testing Tool, Grammarly, Grapeshot, GTmetrix, Heritrix, Heureka Feed, HTTPMon, HubPages, HubSpot, ICC-Crawler, ichiro, IDG/IT, IIS Site Analysis, Inktomi Slurp, inoreader, IP-Guide Crawler, IPS Agent, Kaspersky, Kouio, Larbin web crawler, LCC, Let's Encrypt Validation, Lighthouse, Linkdex Bot, LinkedIn Bot, LTX71, Lycos, Magpie-Crawler, MagpieRSS, Mail.Ru Bot, masscan, Mastodon Bot, Meanpath Bot, MetaInspector, MetaJobBot, MicroAdBot, Mixrank Bot, MJ12 Bot, Mnogosearch, MojeekBot, Monitor.Us, Munin, Nagios check_http, NalezenCzBot, nbertaupete95, Netcraft Survey Bot, netEstate, NetLyzer FastProbe, NetResearchServer, Netvibes, NewsBlur, NewsGator, NLCrawler, Nmap, Nutch-based Bot, Nuzzel, oBot, Octopus, Omgili bot, Openindex Spider, OpenLinkProfiler, OpenWebSpider, Orange Bot, Outbrain, PagePeeker, PaperLiBot, parse.ly, Petal Bot, Phantomas, PHP Server Monitor, Picsearch bot, PingAdmin.Ru, Pingdom Bot, Pinterest, PocketParser, Pompos, PritTorrent, PRTG Network Monitor, QuerySeekerSpider, Quora Link Preview, Qwantify, Rainmeter, RamblerMail Image Proxy, Reddit Bot, Riddler, Robozilla, Rogerbot, ROI Hunter, RSSRadio Bot, SafeDNSBot, Scooter, ScoutJet, Scrapy, Screaming Frog SEO Spider, ScreenerBot, Semantic Scholar Bot, Semrush Bot, Sensika Bot, Sentry Bot, Seobility, SEOENGBot, SEOkicks-Robot, Seoscanners.net, Serendeputy Bot, Server Density, Seznam Bot, Seznam Email Proxy, Seznam Zbozi.cz, ShopAlike, Shopify Partner, ShopWiki, SilverReader, SimplePie, SISTRIX Crawler, SISTRIX Optimizer, Site24x7 Website Monitoring, Siteimprove, SiteSucker, Sixy.ch, Skype URI Preview, Slackbot, SMTBot, Snapchat Proxy, Sogou Spider, Soso Spider, Sparkler, Speedy, Spinn3r, Spotify, Sprinklr, Sputnik Bot, sqlmap, SSL Labs, Startpagina Linkchecker, StatusCake, Superfeedr Bot, Survey Bot, Tarmot Gezgin, TelegramBot, The Knowledge AI, theoldreader, TinEye Crawler, Tiny Tiny RSS, TLSProbe, TraceMyFile, Trendiction Bot, TurnitinBot, TweetedTimes Bot, Tweetmeme Bot, Twingly Recon, Twitterbot, UkrNet Mail Proxy, UniversalFeedParser, Uptimebot, Uptime Robot, URLAppendBot, Vagabondo, Velen Public Web Crawler, Vercel Bot, Visual Site Mapper Crawler, VK Share Button, W3C CSS Validator, W3C I18N Checker, W3C Link Checker, W3C Markup Validation Service, W3C MobileOK Checker, W3C Unified Validator, Wappalyzer, WebbCrawler, WebDataStats, Weborama, WebPageTest, WebSitePulse, WebThumbnail, WeSEE:Search, WikiDo, Willow Internet Crawler, WooRank, WordPress, Wotbox, XenForo, YaCy, Yahoo! Cache System, Yahoo! Japan BRW, Yahoo! Link Preview, Yahoo! Slurp, Yahoo Gemini, Yandex Bot, Yeti/Naverbot, Yottaa Site Monitor, Youdao Bot, Yourls, Yunyun Bot, Zao, Ze List, zgrab, Zookabot, ZumBot

## Built with

* [Matomo device detector](https://github.com/matomo-org/device-detector) - A powerful device detection library.
* [node.js](https://nodejs.org/en/) - Cross-platform JavaScript run-time environment for executing JavaScript code server-side. 
* [TypeScript](https://www.typescriptlang.org/) - Typed superset of JavaScript that compiles to plain JavaScript.
* [Jest](https://facebook.github.io/jest/) - Delightful JavaScript Testing.

## Contributing

When contributing to this project, please first discuss the change you wish to make via issue, email, or any other method with the owners of this repository before making a change.

Update the [README.md](https://github.com/etienne-martin/device-detector-js/blob/master/README.md) with details of changes to the library.

Execute `yarn test` and update the [tests](https://github.com/etienne-martin/device-detector-js/tree/master/src/tests) if needed.

### How to update to a newer version of matomo?

This library needs to be updated when matomo releases a new version of their library. Here's how to proceed: 

1. Pull the master branch from this repo
2. Update the `https://github.com/matomo-org/device-detector#{version-number}` to the latest version of matomo device detector in the package.json
3. Run `yarn fixtures` to update to the latest fixtures. This will download new fixtures based on the version specified in the package.json
4. Run `yarn test` and update the library if some tests are failing
5. Open a PR

### Why do tests fail after downloading new fixtures?

When matomo releases a new version, they usually add support for new brands. [Those brands](https://github.com/matomo-org/device-detector/blob/1060530615c54796cc2045a030c7c605574060d2/Parser/Device/DeviceParserAbstract.php#L65) needs to be copied over to [this file](https://github.com/etienne-martin/device-detector-js/blob/master/src/tests/fixtures/brands.json).  

## Authors

* **Etienne Martin** - *Initial work* - [etiennemartin.ca](http://etiennemartin.ca/)
* **Alex Beauchemin** - *Contributor* - [linkedin.com/in/alexbeauchemin](https://www.linkedin.com/in/alexbeauchemin/)
* **Ayan Dey** - *Contributor* - [linkedin.com/in/dey-ayan](https://www.linkedin.com/in/dey-ayan)
* **Julien Maitrehenry** - *Contributor* - [linkedin.com/in/jmaitrehenry](https://www.linkedin.com/in/jmaitrehenry)

## License

This is a free/libre library under license LGPL v3 or later.
