# 2. A leggyakrabban használt

# komponensek

## 2.1. E lméleti háttér

Az előző fejezetben megismerkedtünk néhány vezérlővel. Ebben a fejezetben a választást
támogató vezérlőkomponensekkel ismerkedünk meg.

**ComboBox vezérlő**

A ComboBox egy szövegdoboz és egy listamező kombinációja. A ListBox osztályból
származik. Annyiban más, mint az őse, hogy nemcsak kiválasztást tesz lehetővé, hanem a
vezérlő szövegdoboz részében új elemeket is megadhatunk, ha az engedélyezett, növelve a
választékot.

A ComboBoxnak is számos publikus tulajdonsága van, ebből az egyik fontos a
DropDownStyle, amely a legördülő lista stílusát állítja be. Az alábbi képen a különböző
stílusbeállítások láthatók. Simple érték esetén nincs legördülő rész, csak a listát látjuk. A
default, alap esetben legördíthető a lista kínálata és a szövegmező részbe beírt új elemmel
bővíthető a lista. A DropDownList tulajdonságérték letiltja a listabővítési lehetőségét, csak a
legördítés lehetséges. A többi tulajdonsága a ListBoxnál már megismert SelectedIndex,
SelectedItem, Items stb. A DropDownHeight tulajdonsággal megadhatjuk a legördülő lista
magasságát.


**Választóvezérlők –** CheckBox

A CheckBox vezérlő egy érték beállítására alkalmas. Rendszerint valamilyen logikai érték
megjelenítésére használjuk. A formra több checkBox objektum is elhelyezhető. Legfontosabb
tulajdonsága a Checked, amely megmutatja, hogy be van-e állítva vagy sem. A Text
tulajdonsága a checkBoxhoz tartozó feliratot tartalmazza.

A CheckState tulajdonsággal három állapot beállítására van lehetőség Checked, Unchecked
és Intermediate, ha a ThreeState tulajdonság értéke True, vagyis megengedett a három
állapot. Legfontosabb eseménye a CheckedChanged esemény.

**A RadioButton vezérlő**

Általában több RadioButton vezérlőt helyezünk a formra, ez több felkínált lehetőség közötti
választást tesz lehetővé. Csak egy RadioButtont lehet választani. Az alábbi képen látható a
működése. Legfontosabb tulajdonsága a Text, ami a felirata és a Checked, ami jelzi, hogy ki
van választva.


Fontos eseménye a CheckedChanged esemény, amely jelzi, hogy megváltozott a kijelölése.

Abban az esetben, ha többféle választékból kell egyet-egyet kiválasztanunk, akkor
csoportosítani kell a RadioButton vezérlőket, és valamilyen konténer típusú vezérlőre kell
felhelyeznünk. Ilyen konténer típusú vezérlő a formon kívül a Panel és a Group vezérlő.

A Group vezérlőnek adhatunk feliratot, Text tulajdonság, s ez futás közben látható. A Group
vezérlőnek nincs AutoScroll tulajdonsága, tehát nem gördíthető. A Panel vezérlőnek nem
adhatunk feliratot, nincs Text tulajdonsága, viszont a BorderStyle, keretstílust beállíthatjuk,
ami futás közben látszik. A Panel vezérlőn görgetősávot be lehet kapcsolni.

**Button (nyomógombvezérlő)**

A leggyakrabban használt vezérlőelem. A Control osztály minden tulajdonságát megörökli. A
Text tulajdonsága a gomb feliratát tartalmazza. Előtér, háttérszíne beállítható. Az Image
tulajdonsága segítségével kép is elhelyezhető rajta. Legfontosabb eseménye a Click
esemény.

**Párbeszéd, dialógusablakok**

A .NET környezetben több beépített dialógusablak van, amelyek megkönnyítik a fejlesztők
munkáját. A fájlok kezelésénél láttuk, hogy meg kell adnunk a fájl nevét, és ha nem a projekt
Bin/Debug mappájában helyeztük el a fájlt, akkor az elérési utat is meg kellett adnunk.
Sokkal könnyebb a falhasználó dolga, ha a fájlokat és mappákat egy párbeszédablakban
adhatja meg.

A dialógusablakok a ToolBox Dialogs csoportjában találhatók meg, ahogy a kép mutatja.


Amikor kiválasztunk egy dialógusablakot és ráhúzzuk a formra, az a komponens tálcára
kerül, nem látszik a formon.

OpenFileDialog **és** SaveFileDialog

Amikor a programból meg akarunk hívni egy fájl Megnyitás vagy Mentés ablakot, akkor előbb
egy objektumpéldányt kell készíteni belőle.

Az objektum létrehozása a konstruktorhívással történik:

OpenFileDialog _változónév_ = new OpenFileDialog ();

SaveFileDialog _változónév_ = new SaveFileDialog ();

Az alábbiakban az OpenFileDialog és SaveFile Dialog legfontosabb tulajdonságait gyűjtöttük
össze:

AddExtension true _–_ ha nem adnak meg kiterjesztést, a DefaultExt tulajdonságban
megadott kiterjesztéssel kezeli a fájlt,

false _–_ nincs automatikus kiterjesztéskezelés

DefaultExt alapértelmezett fájlkiterjesztés

FileName a kiválasztott fájl neve

Filter szűrő a fájltípusok megadására,

az elemeket a pipe (cső) szimbólummal ( | -vel) elválasztva

InitialDirectory kezdeti könyvtár beállítása

Title a fejléc szövege

ValidateNames true _–_ ellenőrzi, csak érvényes karakterek szerepelnek-e a
fájlnévben
false _–_ nincs ellenőrzés.


Az alábbi képen a SaveFile Dialog tulajdonságai láthatók

Legfontosabb eseménye a FileOK esemény, amely akkor következik be, amikor a
felhasználó az Open vagy a Save gombra kattint.

A párbeszédablakok a ShowDialog() metódus hívásával jeleníthetők meg, vagyis modális
ablakként fut. A metódushívás visszatérési értéke a DialogResult, amely megadja, milyen
nyomógombot választottunk a párbeszéd lezárásához.

**Vezérlők dinamikus kezelése**

A következő egyszerű példában bemutatjuk, hogyan készíthető olyan alkalmazás, ahol futás
közben tesszük a formra a vezérlőelemeket.

Készítsünk egy programot, amelyben a felhasználó megadja az összeadandók számát. A
nyomógombra kattintást követően felkerül annyi szövegdoboz az űrlapra, ahány értéket


össze szeretne adni a felhasználó. A **Számol** gombra kattintáskor megjelenik az eredmény
is. Az induló felület a következő:

Egy futási eredmény a következő ábrán látható

A Form kezdeti tulajdonságait a konstruktorban állítjuk be, így az átméretezhetőség
engedélyezését, a kezdőpozíciót. Osztályszinten deklarálunk egy TextBox típusú listát az
összeadandó számok beviteléhez.


A következő kódrészletben ellenőrizzük, hogy helyesen adta-e meg a felhasználó az
összeadandók számát. Az ellenőrzés while ciklusban történik, s mindaddig nem lépünk ki a
ciklusból, amíg helyes értéket nem kapunk.

Fontos kérdés a Vezérlőelemek megfelelő pozicionálása. Pontosan egymás alatt, megfelelő
függőleges távolságban, az ablak bal szélétől ugyanolyan távolságban kell elhelyezni őket
futásidőben.

A vezérlőelemek futásidőben történő formra helyezését az alábbi kódrészletben követhetjük
nyomon.


Az ábrán a kommentekből jól követhető, hogy mit csinál a program. Először a konstruktor
meghívásával létrehozzuk a szövegdobozokat tartalmazó listaobjektumot. Ezt követően egy
for ciklusban létrehozunk annyi címkét és szövegdobozt, amennyi a felhasználó által
megadott összeadandók száma. Beállítjuk a tulajdonságaikat, különös tekintettel a Location
tulajdonságra. Majd hozzáadjuk a TextBox vezérlőelemeket a textboxok listájához és azután
a textboxokat és a címkéket hozzáadjuk a form vezérlőelemeinek Controls gyűjteményéhez.

Ezt követően már csak a nyomógomb objektumot kell létrehoznunk a megfelelő
tulajdonságértékekkel, majd őt is hozzá kell adni a form Controls gyűjteményéhez.


Természetesen célszerű ellenőrizni, hogy a felrakott szövegdobozok mindegyikébe
megadta-e a felhasználó az összeadandó értékét, vagy sem. Ha hiba van, erről értesítést
kap a felhasználó.

Az Összead nyomógomb eseménykezelője végzi az adatok ellenőrzését és az eredmény
kiszámítását is, melyet egy MessageBoxban jelenít meg.


