# fhem-uwz

fhem-uwz ist ein Modul für fhem mit dem man Unwetterwarnungen von unwetterzentrale.de in fhem integrieren kann.
Zusätzlich zu den Readings werden Widgets für den Floorplan zur Verfügung gestellt.


Installation:
-----------------------------------------
Die Installation erfolgt manuell. Hierfür muss die Datei 77_UWZ.pm in dem Ordner "fhem/FHEM/" abgelegt werden und mittels neustart von fhem oder einem "reload 77_UWZ.pm" eingelesen werden.


Updates:
-----------------------------------------
In fhem kann mit folgendem Kommando das Modul upgedatet werden:

    update 77_UWZ.pm https://raw.githubusercontent.com/tobias-d-oe/fhem-uwz/master/control-uwz.txt


Verwendung:
-----------------------------------------
    define Unwetterzentrale UWZ DE 77777 3600
    define <name> UWZ <Ländercode> <PLZ> <INTERVAL>

Auch ein paar Funktionen zur Benutzung durch weblink sind integriert:

    define UnwetterDetailiert weblink htmlCode {UWZAsHtml("Unwetterzentrale")}
    define UnwetterLite weblink htmlCode {UWZAsHtmlLite("Unwetterzentrale")}
    define UnwetterFloorplan weblink htmlCode {UWZAsHtmlFP("Unwetterzentrale")}
    define UnwetterKarteBY weblink htmlCode {UWZAsHtmlKarteLand("Unwetterzentrale","Bayern")}

Der zweite Parameter kann folgendes sein:

    europa
    deutschland
    deutschland-small
    bayern
    bremen
    baden-wuerttemberg
    brandenburg
    berlin
    hessen
    niedersachsen
    rheinland-pfalz
    saarland
    sachsen
    sachsen-anhalt
    thueringen
    nordrhein-westfalen
    mecklenburg-vorpommern
    schleswig-holstein
    hamburg
    oesterreich
    burgenland
    kaernten
    niederoesterreich
    oberoesterreich
    salzburg
    steiermark
    tirol
    vorarlberg
    wien
    isobaren1
    isobaren2


Readings:

    Warn_0|1|2|3...|9_... - aktive Warnmeldungen
    WarnCount - Anzahl der aktiven Warnmeldungen
    Warn_0_Start - Beginn der Warnung
    Warn_0_Start_Date - Startdatum der Warnung
    Warn_0_Start_Time - Startzeit der Warnung
    Warn_0_End - Warn Ende
    Warn_0_End_Date - Enddatum der Warnung
    Warn_0_End_Time - Endzeit der Warnung
    Warn_0_Severity - Schwere des Unwetters (0 kein Unwetter, 12 massives Unwetter)
    Warn_0_Type - Art des Unwetters
        1 - unbekannt
        2 - Sturm/Orkan
        3 - Schneefall
        4 - Regen
        5 - Extremfrost
        6 - Waldbrand
        7 - Gewitter
        8 - Glätte
        9 - Hitze
      10 - Glatteisregen
      11 - Bodenfrost
    Warn_0_uwzLevel - Schwere des Unwetters (wie Severity)
    Warn_0_levelName - Level Warn Name
    Warn_0_ShortText - Kurzbeschreibung der Warnung
    Warn_0_LongText - Ausführliche Unwetterbeschreibung
    Warn_0_IconURL - Kumulierte URL um Warnungs-Icon von www.unwetterzentrale.de anzuzeigen
    Warn_0_Hail - Hagelwarnung (0|1)


Attribute:

    download [0|1]
    savepath (default:"/tmp/")
    maps (leerzeichen separierte Liste der zu speichernden Unwetterkarten. Siehe UWZAsHtmlKarteLand)
    humanreadable [0|1] (aktiviert Warn_0_Start_Date, Warn_0_Start_Time, Warn_0_End_Date und Warn_0_End_Time.)



