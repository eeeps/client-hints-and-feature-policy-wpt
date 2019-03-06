## Client Hints + Feature Policy tests

Some Web Platform Tests for Client Hints + Feature Policy

- [x] **Enabling third party** `<meta http-equiv="Accept-CH" content="DPR">` + `Feature-Policy: ch-dpr https://third.party` + `<img src="https://third.party/resource">` → should send `DPR`
- [x] **No feature policy at all? Third party disabled by default** `<meta http-equiv="Accept-CH" content="DPR">` + no `Feature-Policy` + `<img src="https://third.party/resource">` → should not send `DPR`
- [x] **Disabling first party** `<meta http-equiv="Accept-CH" content="DPR">` + `Feature-Policy: ch-dpr 'none'` + `<img src="first/party/resource">` → should not send `DPR`
- [ ] **Enabling multiple hints for multiple third parties should work** `<meta http-equiv="Accept-CH" content="DPR, Viewport-Width">` + `Feature-Policy: ch-dpr https://a-third.party https://another-third.party; ch-viewport-width https://a-third.party https://another-third.party; ` + `<img src="https://a-third.party/resource">` + `<img src="https://another-third.party/resource">` → should both send `DPR` and `Viewport-Width`
- [ ] **Enabling for the wrong third party shouldn't work** `<meta http-equiv="Accept-CH" content="DPR, Viewport-Width">` + `Feature-Policy: ch-dpr https://a-third.party` + `<img src="https://another-third.party/resource">` → should not send `DPR`
- [ ] **Enabled in an iframe + parent frame should work**
- [ ] **Enabled in an iframe but not in the parent frame should not work**
