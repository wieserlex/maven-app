### Installation von Maven
Erfolgte bei mir auf Mac ganz einfach über Homebrew.
    
    ```
    brew install maven
    ```


### Ausführen von Maven-Tools
**Maven-Phasen**  
Obwohl dies keine umfassende Liste ist, sind dies die häufigsten Standard-Lebenszyklusphasen, die ausgeführt werden:

- **validate**: Überprüft, ob das Projekt korrekt ist und alle notwendigen Informationen verfügbar sind.
- **compile**: Kompiliert den Quellcode des Projekts.
- **test**: Testet den kompilierten Quellcode mithilfe eines geeigneten Unit-Test-Frameworks. Diese Tests sollten nicht erfordern, dass der Code gepackt oder bereitgestellt wird.
- **package**: Nimmt den kompilierten Code und packt ihn in sein vertriebsfähiges Format, z. B. in ein JAR.
- **integration-test**: Verarbeitet und stellt das Paket bei Bedarf in einer Umgebung bereit, in der Integrationstests durchgeführt werden können.
- **verify**: Führt alle Überprüfungen durch, um sicherzustellen, dass das Paket gültig ist und die Qualitätskriterien erfüllt.
- **install**: Installiert das Paket im lokalen Repository, damit es lokal als Abhängigkeit in anderen Projekten verwendet werden kann.
- **deploy**: Wird in einer Integrations- oder Release-Umgebung durchgeführt und kopiert das endgültige Paket in das Remote-Repository, um es mit anderen Entwicklern und Projekten zu teilen.

Es gibt zwei weitere Maven-Lebenszyklen, die über die obige Standardliste hinausgehen. Diese sind:

- **clean**: Bereinigt die durch vorherige Builds erstellten Artefakte.
- **site**: Erstellt eine Projektdokumentation.

Phasen sind tatsächlich mit zugrunde liegenden Zielen verknüpft. Die spezifischen Ziele, die pro Phase ausgeführt werden, hängen vom Verpackungstyp des Projekts ab. Zum Beispiel führt **package** `jar:jar` aus, wenn der Projekttyp ein JAR ist, und `war:war`, wenn der Projekttyp – wie du dir denken kannst – ein WAR ist.

Ein interessanter Punkt ist, dass Phasen und Ziele in einer Sequenz ausgeführt werden können.

```bash
mvn clean dependency:copy-dependencies package
```

### Was ist `mvn site`?

Der Befehl `mvn site` generiert eine statische Projektwebsite mit Dokumentation und Berichten zur Codequalität und -tests. Die wichtigsten Funktionen sind:

- **Dokumentation**: Erstellen von Projekt- und Lizenzinformationen.
- **Berichterstellung**: Erzeugt Berichte wie:
    - **Testberichte**: Ergebnisse der Unit-Tests.
    - **Code-Abdeckung**: Testabdeckungsberichte (z.B. mit JaCoCo).
    - **Abhängigkeitsberichte**: Details zu Projektabhängigkeiten.
    - **Checkstyle-Berichte**: Informationen zur Codequalität.

Die generierte Website wird im Verzeichnis `target/site` gespeichert und kann lokal durch Öffnen der Datei `index.html` angesehen werden.

#### Beispiel:
```bash
mvn site