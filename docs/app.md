
# Benachrichtigungen

---

## Einführung

>Push-Benachrichtigungen sind Meldungen, die ohne das Öffnen der jeweiligen App auf dem Smartphone angezeigt werden.

>Notifications, d.h. Benachrichtigungen über den Zeitpunkt des Erscheinens der neuesten Folge einer ausgewählten Serie, werden über [FCM](#FCM NOtifications) (Firebase Cloud Messaging) realisiert.

>Die Kommunikation mit der API zur Abfrage von Serieninformationen funktioniert über HTTP-GET-Abfragen (siehe [API](api.md#API)).

## FCM Notifications

>Damit Benutzer der App Benachrichtigungen erhalten können, muss der im Hintergrund laufende Benachrichtigungs-Service von Android angesprochen werden. Dies geschieht mithilfe von Firebase Cloud Messaging, einem Online-Service bereitgestellt von Google.

Wenn aus der App eine Anfrage für eine Benachrichtigung (z.B. durch das Hinzufügen einer Serie in die eigene Watchlist) an unseren Server über eine HTTP-POST-Anfrage gesendet wird, reagiert dieser durch eine eigene Push-Benachrichtigung via Firebase.

Im Falle einer Anfrage eines Benutzers mit eigenem Account, wird zuerst eine Anfrage an die Firebase Datenbank gestellt, um die persönliche Watchlist zu aktualisieren. Mit dem erhaltenen Token wird nun eine Anfrge an den Server gestellt, die Benachrichtung via FCM auszustellen. Zum Füllen ebendieser Benachrichtigung mit den richtigen Daten, bzw. um die korrekte Überlieferungszeit zu gewährleisten, fragt der Server diese Informationen durch weitere Anfragen wie [getSeriesbyId](API.md#getSeriesById) ab, und die Benachrichtigung wird mit dem gewollten Inhalt zur richtigen Zeit über FCM ausgestellt.

Dabei bietet Google die Firebase Console GUI zum Vereinfachten Testen dieses Vorganges, auch ohne eigenen Server. Diese Funktion kann auch benutzt werden, um einfach und schnell an bestimmte Nutzergruppen der App Benachrichtigungen zu versenden, z.B. nur an Nutzer in bestimmten Ländern oder Altersgruppen.
![](https://firebase.google.com/docs/cloud-messaging/images/messaging-overview.png)

## GUI

## Authentifizierung