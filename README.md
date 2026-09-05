### Chrome extensions that process locally

I build browser extensions that do real work on your own machine — no upload, no
account, no network permission — and then open-source the parts that were hard
to get right.

The recurring theme in all of it: **in Manifest V3, the things that break do so
silently.** The service worker is killed at ~30s idle, `sendMessage` rejects
whenever it's asleep, WASM won't compile without the right CSP, and the store
rejects your images for the wrong reason. None of it produces an error anyone
will ever read. The user just sees a spinner that never stops and leaves one
star.

These repos are the shapes that survive that.

---

**[chrome-ext-offline-license](https://github.com/Kuan-1113/chrome-ext-offline-license)**
· `JavaScript` · `MIT`
Sell paid features with no licence server and no network permission. Keys are
signed offline with ECDSA P-256 and verified in the browser against an embedded
public key — so a "nothing leaves your computer" claim survives the introduction
of a paid tier, which it does not if you add a licence server.

**[mv3-extension-starter](https://github.com/Kuan-1113/mv3-extension-starter)**
· `JavaScript` · `MIT`
An MV3 skeleton with the failure modes already handled: heavy work in an
offscreen document with an idle alarm, `withTimeout` on every message hop,
handlers that always reply, clipboard without the permission prompt, and a build
that ships an allowlist rather than a folder.

**[chrome-webstore-launch](https://github.com/Kuan-1113/chrome-webstore-launch)**
· `Python` · `MIT`
Store assets in the format the store actually accepts, and a preflight that
fails loudly before you upload. Includes the rejection guide — starting with the
fact that *"image has incorrect dimensions"* almost always means an alpha
channel, not the dimensions.

**[pdf-lib-cjk](https://github.com/Kuan-1113/pdf-lib-cjk)**
· `JavaScript` · `MIT`
Write Chinese, Japanese and Korean into a PDF that Chrome will actually draw.
A CFF font embeds as CIDFontType0 and the viewer paints nothing — silently,
while Acrobat renders it fine. The font pipeline that avoids that, plus
subsetting that takes one line of Chinese from 4,370 KB embedded down to 4.7 KB.

---

Also here: some earlier work on quantitative trading tooling
([kuan-trading-skills](https://github.com/Kuan-1113/kuan-trading-skills),
[taiwan-quant](https://github.com/Kuan-1113/taiwan-quant)).

Everything above is MIT. Issues and PRs welcome.
