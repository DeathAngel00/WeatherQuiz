# Video transcript - CIS046-3 (~10 mins) - Banana Quiz

Hi, I'm [name]. This is my Banana quiz. Login is Ada / hello23.

## 0:00-1:00 demo

I run run.bat from the repo root. It builds and opens the login. Wrong
password is rejected. Signup makes a hashed user. Session file skips
login next time until it expires. Logout clears it.

Menu has Play banana quiz, Leaderboard, Logout. The quiz shows a live
banana image from the API with a missing number, and I pick 0-9. 20s
timer each. Leaderboard: I see my own scores, Ada the admin sees all.

## 1:00-2:00 architecture + interop

Swing GUI, engine classes, one API over HTTPS, local files. Diagram
in src/docs/architecture.md. Banana request is
api.php?out=csv&base64=yes, reply is base64 image plus int after the
last comma, decoded and shown with ImageIO. 6s timeout and offline
fallback, bundled banana1.png tagged offline. Real samples in
src/docs/evidence.md.

## 2:00-3:45 version control

Git from day 1, GitHub WeatherQuiz. Small commits, merges to master,
tags v0.1 to v0.3. Engine vs peripherals split kept merges clean.
Team version would use pull requests and review, I self-reviewed diffs.

## 3:45-5:30 events

Buttons are ActionEvents in one actionPerformed: digit answers, skip,
save, menu, logout. Timer is a Swing Timer each second plus a
one-shot pause before the next question. All on the event thread.
The API fetch runs on a SwingWorker so the window never freezes while
loading.

## 5:30-7:15 identity

SHA-256 plus per-user salt in users.txt, never plain. Session file
with UUID and 30min expiry like a cookie. Roles: Ada is admin, signups
are user, column in the file with old files defaulting to user.
Leaderboard filters by role, and role is never taken from a form.
SHA-256 once is weak vs bcrypt, file perms are default, real app wants
a DB.

## 7:15-9:15 evaluation

Banana CSV was picked for one-fetch images, no second request needed.
Splitting on the last comma is simple but breaks if the format
changes, the offline fallback covers that. File sessions are simple
but stealable, expiry limits it. If more time: bcrypt, a DB, more
admin pages.

## 9:15-10:00 close

Runs from run.bat, Java 17. Git history shows steps. Refs in comments
and README. Thanks.

Refs: TomatoFull example (Marc Conrad), Banana API docs, stackoverflow
threads, login-form blog, unit slides.
