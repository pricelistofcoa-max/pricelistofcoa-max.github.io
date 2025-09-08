<html lang="eng">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Basit Başlık Sayfası</title>
  <style>
    /* Temel reset */
    *, *::before, *::after { box-sizing: border-box; }
    html, body { height: 100%; margin: 0; padding: 0; }/* Arka plan siyah */
body { background: #000; color: #fff; font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; }

/* Sabit header - köşelere yapışacak */
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  /* iPhone notches / safe areas için yüksekliği safe-area ile birlikte hesapla */
  height: calc(60px + env(safe-area-inset-top));
  padding-top: env(safe-area-inset-top);
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(180deg, #7b3fe4 0%, #5b1db8 100%); /* hoş mor tonları */
  color: white;
  margin: 0;
  z-index: 9999;
}

/* Başlık içinde arada boşluk kalmaması için kenar boşlukları safe-area ile ayarlı */
header .inner {
  width: 100%;
  padding-left: env(safe-area-inset-left);
  padding-right: env(safe-area-inset-right);
  display: flex;
  align-items: center;
  justify-content: center;
}

/* İçerik kısmı - header yüksekliği kadar yukarıdan başlasın */
main {
  /* header yüksekliğinin aynısını boşluk olarak bırak (mobile safe-area uyumlu) */
  padding-top: calc(60px + env(safe-area-inset-top));
  height: calc(100vh - (60px + env(safe-area-inset-top)));
  display: flex;
  align-items: flex-start; /* header altından hemen başlasın */
  justify-content: center;
}

/* "Welcome" metni */
.welcome {
  margin: 16px 0 0 0; /* header altından biraz aşağı */
  font-weight: 600;
  font-size: clamp(20px, 5vw, 40px); /* responsive font */
  line-height: 1.1;
  color: #fff;
}

/* Sayfada başka bir şey olmasın, bu stil fazladan eleman eklenmesini de kontrol eder */
body * { -webkit-tap-highlight-color: transparent; }

  </style>
</head>
<body>
  <header>
    <div class="inner">
      <!-- Header içinde yalnızca mor arka plan ve boşluk yok -->
      <span aria-hidden="true"></span>
    </div>
  </header>  <main>
    <h1 class="welcome">Welcome</h1>
  </main>
</body>
</html>
