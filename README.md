# LaTeX SOČ šablona
Když jsem měl psát soč zděsil jsem se jejich [šablony](https://www.soc.cz/dokumenty/sablona_SOC.docx), nakonec jsme našli [LateX šablonu](https://github.com/RoboticsBrno/soctemplate/) a tu upravili dle místních zvyklostí.

## LaTeX
LaTeX("latech" nikoliv "lateks") umožňuje autorům textů sázet a tisknout svá díla ve velmi vysoké kvalitě, přičemž autor používá "profesionály" předdefinovaných vzhledů dokumentu. Ty jsi se k dokumentu už dostal. Je v tomhle repozitáři, stáhnout si ho můžeš [tady]() a s ním dále pracovat. __POZOR__ nejde ho jen tak upravovat, po změně se musí znovu "sestavit"/přeložit. K tomu potřebuješ speciální program. My používáme [overleaf](https://www.overleaf.com), který toho umí mnohem víc než jen upravovat LaTeX.

## Začínáme
Teď tě rychle provedeme přípravou a nahráním projektu do overleafu.
- Jdi na [www.overleaf.com](https://www.overleaf.com) a zaregistruj se
- stáhni si tenhle repositář [tady]()
- přihlas se do overleafu, měl by jsi vidět stránku s projekty
- klikni na "New Project" a vyber upload project
- nahraj stažený *zip*

Hurá! Projekt jsme nahrály, teď jenom dodělat náležitosti.
- otevři si soubor *text.tex*, to je hlavní kostra práce
- změň všechen text ve složených závorkách *{}* s prefixem *TODO:*
  - můžeš použít klávesovou zkratku *Ctrl + f*, která vyhledává slova v dokumentu
  - všechny pole by měli být popsány
## Komentáře
Pokud chceš něco "zneviditelnit", můžeš to zakomentovat třemi procenty **%%%** cokoliv je na řádku za nimi, bude vidět jenom v editoru
Možná komentáře znáš z pythonnu(*#*), C#(*//*) nebo HTML(*<!--  -->*)

## Kapitoly
> ["divide et impera"](https://cs.wikipedia.org/wiki/Rozd%C4%9Bl_a_panuj)
Už jsi viděl *text.tex*, hlavní kostru a možná jsi si všiml bloků
```
%%% Závěr
\input{05zaver.tex}
```
Ty jsou tu proto, abychom se v dokumentu vyznali. Každá kapitola má vlastní soubor. My je formátujeme stylem *00uvod.tex*, *01nazevPrvniKapitoly.tex* atd.
Jak takové soubory vypadají se můžeš podívat, pár jsme jich tam nechali. *00uvod.tex* a *99zaver.tex* určitě nemaž, budeš je taky potřebovat.
### Jak vytvořit novou kapitolu
- *Create new file*
- pojmenuj ji podle konvence
- přidej
```
%%% Název kapitoly
\input{nazev vytvorene slozky}
```
- Kapitoly přidávej chronologicky -> záleží na pořadí bloků
### Členění
- Každá kapitola musí začínat ```\hypertarget{jmenoKapitoly}{\chapter{Jméno}}```, tím se vygeneruje velký nadpis a přidá se do obsahu (1.0).
- Podkapitoly značíme ```\section{jméno}``` (1.1)
- Podpodkapitoly značíme ```\subsection{jméno}``` (1.1.1)
- Podpodpodkapitoly a další se značí přidáním dalšího *sub*(```\subsubsection{jméno}```), ale to ti u vedouc9ho pr8ce neprojde :D

### Odkazy na kapitoly
Při psaní můžeš narazit na něco, co se vyskytuje v jiné kapitole. Potom je dobré vytvořit v elektronické verzi proklik.
```\hyperlink{jmenoKapitoly}{Viditelný text odkazu}.```

## Poznámky pod čarou
U nás velmi oblíbená věc, kdo nemá poznámky pod čarou, pro Dvořku neexistuje. S LaTeXem jseou jednoduché.
```\footnote{Text poznámky pod čarou}```
Kód píšeme hned za slovo, ke kterému se poznámka vztahuje. LaTeX ji očísluje a zařadí pod čáru.

## Obrázky
Bez obrázků se asi taky neobejdeš, tady je to trochu složitější. Nejdřív nahraj obrázek do složky *img*.
```
\begin{figure}[H]
    \centering
    \includegraphics{img/nazevSouboru}
    \caption{popis obrázku}
\end{figure}
```
Někdy jsou obrázky moc velké a dělají neplechu, potom je dobré jim nastavit šířku. Správnou hodnotu najdeš experimentálně. Nám se osvědčilo 300px
```
\begin{figure}[H]
  	\centering
 	\includegraphics[width=300px]{img/drv8833.png}
 	\caption{Schématická značka DRV8833PW nakreslená v~KiCadu}
\end{figure}
```
Obrázky jsou automaticky centrované.
## Citace
Strašák všech studentů, najít všechny údaje, otevřít *citace.com*, vygenerovat, zkopírovat atd.
V LaTeXu se citace zapisují do souboru *text.bib*. Nechali jsme ti tam několik příkladu pro inspiraci, ale vše by mělo být jasné.
```
@BOOK{Malina1,
  title = {Poznáváme elektroniku I.},
  publisher = {České Budějovice, Kopp},
  year = {2009},
  author = {Václav MALINA},
  isbn = {978-80-7232-376-0 },
}
```
Nejzajímavější je první slovo, *Malina1*, to je interní název knihy. Bude se hodit, pokud na zdroj chceš odkázat v textu. Prostě za odkaz napíšeš
 ```
 \cite{Malina1}
 ```
 a LaTeX vytvoří odkaz.
 ```
 k~jejich ovládání je použit čip DRV8833\cite{DRV8833}
 ```
 
 ## Zvýraznění textu
 Je dobré důležité věci zvýraznit, názvy zešikmit a podobně, k tomu jsou následující značky:
 - \textbf{**tučný**}
 - \underline{podtržený}
 - \textit{*kurzíva*}
 
 ## Podpora
 Už znáš asi všechno důležité. Projekt je pod MIT licencí, takže "as is" a veškerá podpora se bude řídit mojí náladou. Budu se snažit pomoci se vším, ale nezvládnu to 24/7. S použitím šablony musíš počítat, že když v ní něco rozbiješ, bude to chvíli rozbité. Jestli tě zajímá něco víc, koukni se nejdřív na [dokumentaci](https://www.overleaf.com/learn/latex/Main_Page)
 
 Jak kontaktovat podporu:
 - ideálně vytvořit **issue** tady na githubu
 - napsat email na pavel@niners.cz
 - napsat mi na [FB](https://www.facebook.com/pavel.srytr)
