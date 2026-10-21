# אתר מרכז אֹופֶק

אתר המרכז הלאומי לחדשנות בחוסן, טראומה ובריאות הנפש של ילדים ומשפחות.
האוניברסיטה העברית · מכון חרוב

**אתר חי:** https://swinnovation.co.il

## מבנה

| קובץ | תפקיד |
|---|---|
| `public/index.html` | האתר כולו — עמוד אחד, דו־לשוני (עברית/אנגלית) |
| `firebase.json` | הגדרות Firebase Hosting |
| `firestore.rules` | הרשאות למסד התוכן |
| `storage.rules` | הרשאות לתמונות ולסרטונים |
| `.github/workflows/firebase-hosting.yml` | פריסה אוטומטית בכל דחיפה ל‑main |

## איך זה עובד

התוכן (טקסטים, קבוצות, אירועים, יישום, צוות) **אינו** בקובץ אלא ב‑Firestore,
ונערך דרך האתר עצמו: כפתור ✎ בסרגל העליון או "כניסה לעריכה" בתחתית העמוד.
הכניסה מנוהלת ב‑Firebase Authentication (Build → Authentication → Users).
תמונות וסרטונים שמועלים במצב עריכה נשמרים ב‑Firebase Storage.

לכן `index.html` הוא המעטפת בלבד — שינוי תוכן אינו דורש דחיפה למאגר.

## פריסה

כל דחיפה ל‑`main` מפעילה את ה‑GitHub Action ומעלה את האתר.

להפעלה חד־פעמית של האוטומציה, מתוך תיקייה מקומית של המאגר:

```
npx firebase-tools init hosting:github
```

הפקודה יוצרת את ה‑Secret בשם `FIREBASE_SERVICE_ACCOUNT_OFEKCENTER_924FD` במאגר.

פריסה ידנית, אם צריך:

```
npx firebase-tools deploy
```
