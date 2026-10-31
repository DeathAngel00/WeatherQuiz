# week8 demo - what to show tutor
- run src/run.bat, login Ada/hello23
- show wrong password rejected
- signup new user, login
- play 2 rounds, show score + tries, keyboard 0-9, timer
- disconnect net to show offline fallback (or point at code)
- open users.txt to show hashed, not plaintext
- git log --oneline --graph, git branch, tag v0.1-week8-demo
- ask tutor to confirm evidence

# video plan (10 min max)
0-1:30 demo login + game
1:30-3:30 version control: branches auth-hashing, interop-fix, gui-events, commits, modular engine vs peripherals
3:30-5:30 events: ActionListener buttons/logout, KeyListener keys, Timer, how dispatch thread works
5:30-7:30 interop: HTTPS GET csv+base64, decoding, ImageIO, timeouts, offline fallback, why not SOAP/REST json
7:30-9:30 identity: SHA-256+salt vs plaintext, users.txt, session.cookie like cookie, 30min expiry, logout, what next (bcrypt, DB)
9:30-10: wrap + refs

# caps to avoid
- week8 show: DONE via tag above
- code zip submitted separately, not just video
- own voice, no heavy editing
- code runs against case study
