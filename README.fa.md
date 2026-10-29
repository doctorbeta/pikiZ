<div dir="rtl">

<p align="center">
  <img src="logo.png" width="128" alt="Piki Zed">
</p>

<h1 align="center">Piki Zed</h1>

<p align="center">همهٔ راه‌های عبور، در یک برنامه.</p>

<p align="center">
  <a href="https://github.com/doctorbeta/pikiZ/releases/latest"><img src="https://img.shields.io/github/v/release/doctorbeta/pikiZ?style=flat-square&color=C7F24E&labelColor=15170B&label=release" alt="آخرین نسخه"></a>
  <img src="https://img.shields.io/badge/Android%20%C2%B7%20Linux%20%C2%B7%20Windows%20%C2%B7%20macOS-C7F24E?style=flat-square&labelColor=15170B" alt="اندروید، لینوکس، ویندوز، مک">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-AGPL--3.0-C7F24E?style=flat-square&labelColor=15170B" alt="AGPL-3.0"></a>
</p>

<p align="center"><a href="README.md">English</a> · <b>فارسی</b></p>

## Piki Zed چیست؟

Piki Zed (پیکی زد) یک کلاینت VPN و پروکسی برای اندروید، لینوکس، ویندوز و مک است که به‌جای یک هسته، چند هسته
را با هم دارد. وقتی یک مسیر بسته شود، مسیر بعدی از قبل نصب است: Xray و sing-box برای پروتکل‌های
رایج، سایفون و Tor برای وقتی که هیچ چیز دیگری وصل نمی‌شود، تونل DNS برای شبکه‌هایی که جز DNS
تقریباً چیزی رد نمی‌کنند، و WireGuard و AmneziaWG و OpenConnect و IKEv2 برای سرورهایی که خودتان
دارید. هسته‌ها را می‌شود از داخل هم عبور داد، و با یک لمس همهٔ سرورها تست می‌شوند و اتصال روی
سریع‌ترینشان می‌رود.

Piki Zed فورکی از [ZedSecure](https://github.com/CluvexStudio/ZedSecure) ساختهٔ CluvexStudio است که با نام و نشان پیکی
منتشر می‌شود. هستهٔ اصلی برنامه کار سازندگان ZedSecure است و طبق AGPL-3.0 در دسترس است.

## هسته‌ها

| هسته | چه چیزی را حمل می‌کند |
|---|---|
| Xray | VLESS با Reality و Vision و XHTTP، VMess، Trojan، Shadowsocks، Hysteria2، WireGuard، AmneziaWG |
| sing-box | TUIC، Naive، AnyTLS، ShadowTLS، فایل‌های OpenVPN (`.ovpn`) و JSON خودِ sing-box |
| سایفون | شبکهٔ خودِ سایفون؛ سرور شخصی لازم ندارد |
| Tor | پل‌های obfs4 و Snowflake و Conjure |
| تونل DNS | DNSTT، VayDNS و MasterDNS، روی UDP یا TCP یا DoT یا DoH |
| OpenConnect | سرورهای Cisco AnyConnect و سازگارها |
| IKEv2 | کلاینت IPsec داخلی خودِ اندروید |
| SSH | به‌تنهایی، یا از داخل هر کدام از بالایی‌ها |

اندروید همه را دارد. لینوکس و ویندوز و مک، Xray و sing-box و تونل‌های DNS و SSH را دارند.

## امکانات

- وارد کردن لینک، اشتراک، JSON خودِ Xray و sing-box، فایل `.ovpn`، لینک `vpn://` امنزیا و کد QR
- انتخاب خودکار: تونل را روی سریع‌ترین سرور نگه می‌دارد و اگر قطع شد خودش جابه‌جا می‌کند
- زنجیره در هر دو جهت، مثلاً Xray از داخل Tor یا Tor از داخل Xray
- مسیریابی برای هر برنامه، ویرایشگر قوانین geoip/geosite، و SNI spoofing روی گوشی‌های روت‌شده
- Vault: کانفیگ را به‌صورت فایل `.zsx` به اشتراک بگذارید تا بدون نمایش محتوا وصل شود، با رمز و تاریخ انقضای اختیاری
- تست سرعت، یافتن MTU، اسکنر DNS و لاگ زنده
- طراحی Material 3 Expressive، روشن و تاریک، به فارسی، انگلیسی، روسی و چینی

## دانلود

**اندروید:** APK مخصوص دستگاهتان را از [Releases](https://github.com/doctorbeta/pikiZ/releases/latest)
همین ریپو بگیرید (`arm64-v8a` برای تقریباً همهٔ گوشی‌ها، `armeabi-v7a` برای گوشی‌های قدیمی‌تر).
نصب از بیرون گوگل پلی لازم است اجازهٔ «نصب برنامه از منبع ناشناس» را برای مرورگر یا مدیر فایل‌تان بدهید.

**لینوکس، ویندوز و مک:** اگر در Releases نسخهٔ آماده نبود، از سورس بسازید (پایین‌تر).

## ساخت از سورس

<div dir="ltr">

```sh
./tools/get-cores.sh android     # or linux, windows, macos-arm64, macos-x86_64
./gradlew :app:assembleRelease   # three APKs, one per ABI
./gradlew :desktop:packageDeb    # or packageRpm, packageMsi, packageDmg
```

</div>

همهٔ هسته‌ها در [ZedSecure-Cores](https://github.com/CluvexStudio/ZedSecure-Cores) ساخته می‌شوند؛
برای هر هسته یک workflow، از فورک‌ها و کامیت‌های دقیقی که در `pins.txt` آن آمده است.
[`tools/cores.txt`](tools/cores.txt) نشان می‌دهد هر نسخه کدام بیلد را برمی‌دارد. زدن تگ `v*` نسخهٔ
اندروید و همهٔ نسخه‌های دسکتاپ را در CI می‌سازد و همه را در یک ریلیز می‌گذارد؛ اندروید و دسکتاپ یک
شمارهٔ نسخه دارند.

**ساخت بدون کامپیوتر:** در تب Actions همین ریپو، workflow با نام `piki-build` را با Run workflow اجرا کنید؛ APK امضاشده در بخش Artifacts همان اجرا ساخته می‌شود. برای انتشار برای دیگران، کلید امضای خودتان را در Secrets بگذارید (`KEYSTORE_BASE64`، `KEYSTORE_PASSWORD`، `KEY_ALIAS`، `KEY_PASSWORD`) و keystore را هرگز commit نکنید.

## سپاسگزاری

Piki Zed بر پایهٔ [ZedSecure](https://github.com/CluvexStudio/ZedSecure) ساختهٔ CluvexStudio ساخته شده است؛ سپاس از سازندگان آن.

حالت‌های DNSTT و VayDNS تونل DNS با کتابخانهٔ [VayDNS](https://github.com/net2share/vaydns)
ساخته شده‌اند که فورکی از [dnstt](https://www.bamsoftware.com/software/dnstt/) است. حالت MasterDNS
موتور جداگانه‌ای است که پایین‌تر از آن نام برده شده.

ایده‌های اصلی این تونل از [SlipNet](https://github.com/anonvector/SlipNet) ساختهٔ anonvector
آمده است: DNS روی TCP ساده (که VayDNS به‌تنهایی ندارد)، حالت‌های رزالور fan-out و round-robin
همراه با تعداد پخش، استخر DNS که در هر اتصال سریع‌ترین رزالورها را انتخاب می‌کند، تنظیمات
override سراسری رزالور و جلوگیری از fallback ی DNS، و طراحی و متن تنظیمات DNS و SSH.

نسخه‌های پیش از 3.0.9 موتور خود SlipNet، از جمله لایهٔ انتقال TCP آن، را داخل هسته داشتند. از
نسخهٔ 3.0.9 موتور `zeddns` است که برای همین اپ نوشته شده؛ همان قابلیت‌ها را دارد، اما با کد
خودش.

ZedSecure (و در نتیجه Piki Zed) همچنین روی
[Xray-core](https://github.com/XTLS/Xray-core)، [sing-box](https://github.com/SagerNet/sing-box)،
[سایفون](https://github.com/Psiphon-Labs/psiphon-tunnel-core)، [Tor](https://www.torproject.org/)،
[MasterDnsVPN](https://github.com/masterking32/MasterDnsVPN)،
[AmneziaWG](https://github.com/amnezia-vpn/amneziawg-go)،
[OpenConnect](https://www.infradead.org/openconnect/)،
[hev-socks5-tunnel](https://github.com/heiher/hev-socks5-tunnel) و
[zeptun](https://github.com/Noisemux/zeptun) بنا شده است. لایسنس هر کدام در
[NOTICE](NOTICE) آمده است.

## لایسنس

Piki Zed مانند ZedSecure تحت [AGPL-3.0](LICENSE) منتشر می‌شود و سورس کامل این نسخه در همین ریپو در دسترس است. هستهٔ برنامه sing-box و سایفون و sing-openvpn را هم لینک می‌کند که GPL-3.0
هستند؛ بند ۱۳ لایسنس GPL-3.0 ترکیب آن‌ها با کد AGPL-3.0 را اجازه می‌دهد و هر بخش لایسنس خودش را نگه می‌دارد.

</div>
