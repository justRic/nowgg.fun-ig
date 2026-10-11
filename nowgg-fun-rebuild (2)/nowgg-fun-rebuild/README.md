# nowgg.fun rebuild — 1:1

Static front-end that mirrors https://nowgg.fun and hops into the live IP-prefix proxy.

## Flow (matches original)
1. Homepage loads → WebRTC STUN probe gets first IP octet → sessionStorage `prefix`
2. Click app → launcher (720p / 30fps defaults)
3. Launch → shows bottom bar "loading, be patient." + discord/frogies links
4. Navigates to: `https://{prefix}.ip.nowgg.fun{path}?params`
5. Live proxy serves the now.gg player session

## Paths (exact)
```
/apps/a/19900/b.html              Road Block
/apps/a/10011/b.html              Stumble Guys
/apps/a/10008/b.html              COD
/apps/a/10019/b.html              Cookie Run
/apps/aptoide/5874/aptoide.html   Aptoide (+ deep_link for Fortnite/Minecraft)
/apps/playducky/7199/melon-sandbox.html
/apps/uncube/7074/now.html
/apps/robtop-games/1400/geometry-dash.html
/apps/psyonix-studios/4656/rocket-league.html
```

## Run
```bash
cd nowgg-fun-rebuild
python3 -m http.server 8080
# open http://localhost:8080
```

Needs browser with WebRTC enabled (same requirement as original).
If probe fails, fallback prefix `1` is used so hop still attempts.
