
== Raffinerie Heide – GEKOL (Hamburg) ==

'''23.10.15 - Die Strecke nach GEKOL ist deaktiviert ! Aber wir bekommen die Daten trotzdem für die andere! '''

'''''Die Daten werden teilweise auch hier gesendet''''' : 
[[TitleIndex(ISO/project/mpks/steckbriefe/RFH_GEK, depth=1)]]

== Quelle ==

    * Partner: RFH
    * MPKS-Nummer: 21
    * Ansprechspartner: Siehe Kontakt [wiki:/ISO/project/mpks/kontaktodex/raffinerieheide Raffinerie Heide]
    * Technik: FTP-MINOVA (mpks_rfheide@ftp.minova.com/in)
    * Dateiformat: z.B. gekol.mpksout.20170724.160011.071
    * Ort (MINEDISRV): \\minedisrv\minova\import\RFH\GEK\

== Versandpaket ESSO – GEKOL (Hamburg) ==

    * Partner: GEKOL
    * MPKS-Nummer: 97
    * Ansprechspartner Daten: [wiki:/ISO/project/mpks/kontaktmpks/gekol-97 GEKOL]
    * Dateiformat: T21_0031097*.DAT
    * Ort (MINEDISRV): \\minedisrv\minova\export\RFH\GEK\


== Selektion ==

 * Alle Sätze 

== Änderungen in der Empfangsdatei: ==

 * In dem Datensatz mit Satzart = 2 werden die Werte in den Datenfeldern "Menge kg", "Menge L 15°C", "Menge Verladel.", "Verladetemp." konvertiert. ( ohne Vorzeichencodierung )

== Properties ==
{{{
# Alle Datensätze 
# select=.{19}(000061).{90}(0330002|0330003|0330004).{38}
#
# Falls das Datenfeld "Auftragstyp" gleich "10" ist, 
# bekommt das Datenfeld "Auftragstyp" den Wert "01"
change.1.select=(.{43})(10)(.{115})
change.1.replace=$101$3
#
#Falls das Datenfeld "Auftragstyp" gleich "11" ist, 
# bekommt das Datenfeld "Auftragstyp" den Wert "02"
change.2.select=(.{43})(11)(.{115})
change.2.replace=$102$3

# #21317 Sonderanschreibung immer lÃ¶schen
change.3.select=(.{135})(.{15})(.{10})
change.3.replace=$1               $3

# #26504 Produktcodes auf "403411" umsetzen
# falls die Lieferstelle 343001 und
# die Ladestammnummer 8305945,8309037,8307681,8306146,8306856,8306863 ist
change.4.select=(.{19})(343001)(.{12})(.{6})(.{72})(8305945|8309037|8307681|8306146|8306856|8306863)(.{38})
change.4.replace=$1$2$3403411$5$6$7
}}}



== Abrechnung SIS ==
||Feld||Wert||
||Kunde||MAROL||
||Kontrakt||EDI-MAROL||
||Projekt||EDI||
||Aufwand||Z-WARTUNG||

 * Beschreibung: Abholungen der Raffinerie Heide GEKOL
 * empfangene Sätze : EDIRI  1 Satz pro Monat
 * abgehende Sätze : EDIRO  1 Satz pro Monat
 * Grundgebühr: MPKS: ESSO-GEKOL

== Streckenname ==

 * Empfänger: RFH_GEK.REC
 * Prüfer: RFH_GEK.PRC
 * Verarbeiter: RFH_GEK.PRC
 * Versender: RFH_GEK
