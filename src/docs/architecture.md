# Architecture - Banana Quiz

```
+--------+   button/timer events      +-----------------+   HTTPS GET   +----------------+
| Swing  | ------------------------> | QuizEngine /    | ------------> | Banana API     |
| GUI    | <------------------------ | BananaFetch /   |  CSV+Base64   | marcconrad.com |
| Menu,  |      image + solution     | Board           |               +----------------+
| Quiz,  |                           |                 |      files
| Login  |                           +-----------------+      v
+--------+                                |        users.txt (salt+hash+role)
    | login/session                       |        session.cookie (token+expiry)
    v                                     +------> scores.txt
+-----------+
| LoginData |
+-----------+
```

Flow: login (hash check, session file) -> menu -> quiz. Quiz asks
Banana API over HTTPS, parses the reply, shows it. Answers are Swing
events. Scores go to scores.txt. Admin sees all, users see own.
Offline fallback (banana1.png) if the API is down. See evidence.md
for real requests.
