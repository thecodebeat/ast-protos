# Codebeat Abstract Syntax Tree Protocol Buffers

*Przeczytaj w innych językach: [English](README.md)*

## Wprowadzenie

![Fundusze Europejskie](assets/pl/FE_IR_rgb-1.jpg "Fundusze Europejskie")

Firma code quest sp. z o.o. w latach 2017-2020 realizowała projekt badawczo-rozwojowy o numerze POIR.01.01.01-00-0792/16 w ramach [Programu Operacyjnego Inteligentny Rozwój 2014-2020](https://www.funduszeeuropejskie.gov.pl/strony/o-funduszach/dokumenty/program-inteligentny-rozwoj-dokument/) Narodowego Centrum Badań i Rozwoju. Projekt nosił nazwę "Codebeat - wykorzystanie sztucznej inteligencji w statycznej analizie jakości oprogramowania". Przedmiotem projektu były badania przemysłowe w obszarze wykorzystania sztucznej inteligencji do statycznej analizy jakości oprogramowania, a także opracowanie innowacyjnego zestawu metryk i heurystyk dla nowych języków obiektowych oraz funkcyjnych. Przed rozpoczęciem projektu firma codequest sp. z o.o. zobowiązała się do rozpowszechnienia wyników prac badawczo-rozwojowych między innymi za pośrednictwem oprogramowania bezpłatnego lub oprogramowania z licencją otwartego dostępu. Pliki umieszczone w tym repozytorium zawierają wyniki prac rozwojowych - definicje struktur stanowiących abstrakcję drzew składniowych (AST) będących reprezentacją gramatyki konkretnego języka programowania oraz niezbędnych do wyliczenia miar jakości na drzewach składniowych.

## Opis projektu

Zapraszamy do repozytorium aplikacji Codebeat, która stanowi wszechstronne rozwiązanie do statycznej analizy kodu źródłowego w różnorodnych językach programowania. To repozytorium zawiera pliki definicji Protocol Buffers (proto), będące kluczowym elementem naszej usługi SaaS (Software as a Service) do analizy statycznej.

Nasza usługa oferuje dogłębną analizę kodu źródłowego, wykrywając potencjalne problemy, duplikacje oraz dostarczając cenne wskazówki odnośnie jakości i struktury kodu. Pliki proto w tym repozytorium określają struktury danych, które służą do przedstawiania i przekazywania wyników analiz, metadanych kodu i innych istotnych informacji przez nas przetwarzanych.

Publikujemy pliki `.proto` z kilku powodów:

- **Interoperacyjność**: Dzięki udostępnieniu tych definicji, w przyszłości umożliwimy innym usługom i narzędziom łatwą integrację z naszą platformą analizy, co zapewni kompatybilność i prostotę wymiany danych.
- **Transparentność**: Jesteśmy zwolennikami przejrzystości narzędzi używanych do tworzenia oprogramowania. Udostępniając te pliki proto, dajemy wgląd w strukturę i sposoby przetwarzania danych w naszych analizach.
- **Współpraca ze społecznością**: Zachęcamy społeczność programistów do udzielania się poprzez sugestie i opinie. Dzięki zrozumieniu struktury naszych danych, mogą oni proponować usprawnienia, rozszerzenia lub nawet nowe zastosowania.

W tym repozytorium znajdziesz następujące pliki proto:
- `v1/analyser.proto`: Określa struktury służące do analizy i raportowania kodu źródłowego, takie jak wykrywanie problemów i metryki jakości kodu.
- `v1/ast.proto`: Zawiera definicje związane z drzewami składniowymi (AST - Abstract Syntax Tree), które są niezbędne do zrozumienia struktury składniowej analizowanego kodu.
- `v1/metadata.proto`: Obejmuje różnorodne struktury metadanych, takie jak raporty o błędach, dane o pokryciu kodu testami oraz informacje o pull requestach.

Pliki te są częścią szerszej, prywatnej bazy kodu. Kod implementacyjny po stronie serwera i klienta nie jest publicznie dostępny, jako że stanowi istotę naszego własnego silnika analizy.

Zachęcamy do zapoznania się z plikami proto oraz włączenia ich do swoich projektów. Twoje opinie i wkład są dla nas niezwykle cenne.

## Rozpoczęcie pracy

Ta sekcja zawiera wskazówki dotyczące korzystania z plików buforów protokołu dostępnych w tym repozytorium. Pliki te są kluczowe dla zrozumienia i wykorzystania struktur danych używanych w naszej usłudze SaaS do statycznej analizy kodu.

### Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz zainstalowane:

- Protocol Buffers (ProtoBuf): Musisz mieć zainstalowany kompilator Protocol Buffers (`protoc`), aby wygenerować klasy dostępu do danych w preferowanym języku z plików `.proto`.
- Kompatybilne środowisko programistyczne: Upewnij się, że Twoje środowisko programistyczne obsługuje język, którego planujesz używać do obsługi plików proto.

### Krok po kroku

1. **Klonowanie repozytorium**:
   Rozpocznij od sklonowania tego repozytorium na swoją lokalną maszynę. Użyj następującego polecenia:

	```bash
	git clone [adres-repozytorium]
	```
	
	Zastąp `[adres-repozytorium]` rzeczywistym adresem URL tego repozytorium.

2. **Instalacja kompilatora Protocol Buffers**:
Jeśli jeszcze tego nie zrobiłeś, zainstaluj kompilator Protocol Buffers. Instrukcje znajdziesz na [stronie GitHub Protocol Buffers](https://github.com/protocolbuffers/protobuf).

3. **Generowanie kodu specyficznego dla języka**:
Przejdź do katalogu zawierającego pliki `.proto` i uruchom kompilator Protocol Buffers, aby wygenerować kod w wybranym języku. Na przykład:

	```bash
	protoc --java_out=./java_gen v1/*.proto
	```

	Ta komenda generuje kod Java dla wszystkich plików proto w katalogu `v1`. Zastąp `--java_out` odpowiednią opcją dla Twojego języka.

4. **Integracja wygenerowanego kodu z Twoim projektem**:
Przenieś wygenerowany kod do katalogu źródłowego Twojego projektu. Upewnij się, że rozwiązano wszelkie zależności lub ścieżki importu, aby były zgodne ze strukturą Twojego projektu.

5. **Przykłady użycia**:
Po zintegrowaniu wygenerowanego kodu możesz tworzyć i operować na strukturach danych zdefiniowanych w plikach proto. Przykłady użycia mogą obejmować tworzenie nowego obiektu `Issue`, wypełnianie pól z wyników analizy i serializację do przechowywania lub transmisji.

### Dalsza pomoc

Aby uzyskać bardziej szczegółowe instrukcje dotyczące korzystania z Protocol Buffers, zapoznaj się z [oficjalną dokumentacją](https://protobuf.dev/overview/). Jeśli napotkasz jakiekolwiek problemy lub masz konkretne przypadki użycia, śmiało otwórz zgłoszenie w tym repozytorium, aby uzyskać wsparcie.

## Zawartość
- `v1/analyser.proto`: Plik definiuje struktury do analizy kodu źródłowego, w tym wykrywania problemów, metryk jakości kodu oraz raportowania analiz.
- `v1/ast.proto`: Zawiera definicje reprezentacji drzew składniowych (Abstract Syntax Tree - AST), niezbędne do zrozumienia i analizowania struktury składniowej kodu.
- `v1/metadata.proto`: Obejmuje struktury metadanych związanych z analizą kodu, w tym raporty o błędach, dane o pokryciu testami i szczegóły pull requestów.

## Szczegółowe Opisy

### v1/analyser.proto
Plik `v1/analyser.proto` definiuje zestaw protocol buffers używanych do analizy kodu źródłowego w projekcie. Główne struktury i ich zastosowania to:

- `SourceFile`: Reprezentuje plik źródłowy w projekcie, zawierając jego ścieżkę, skrót zawartości, rzeczywistą treść oraz status ważności.
- `SupportingFile`: Definiuje plik pomocniczy użyteczny w analizie, ale nie przeznaczony do parsowania.
- `Location` i `ExactLocation`: Wskazują lokalizacje różnych elementów w pliku źródłowym, przy czym `ExactLocation` oferuje bardziej precyzyjne pozycjonowanie (takie jak początek i koniec linii).
- `Severity`: Enumeracja reprezentująca wagę problemu lub podobieństwa, waha się od `NONE` do `CRITICAL`.
- `Issue` i `Similarity`: Definiują problemy w kodzie, przy czym `Similarity` koncentruje się na kwestiach związanych z duplikacją kodu.
- `LintIssue` i `LintResult`: Służą do reprezentowania problemów zidentyfikowanych przez lintery i ich wyników.
- `BrakemanIssue` i `BrakemanResult`: Specyficzne struktury dla problemów zidentyfikowanych przez narzędzie analizy Brakeman.
- `GenericIssue`: Opisuje problemy wynikające z wartości eksperymentalnych metryk.
- `Namespace`: Reprezentuje przestrzeń nazw w kodzie, zawierając metryki, funkcje i związane z nimi problemy.
- `Report`: Agreguje wyniki analizy, w tym przestrzenie nazw, pliki źródłowe, pliki pomocnicze oraz różne rodzaje problemów.
- `Error`: Szczegółowo opisuje błędy, które mogą wystąpić podczas analizy, w tym ich rodzaje i informacje do debugowania.
- `Timestamps`: Rejestruje różne znaczniki czasu związane z procesem analizy.
- `GitDetails`: Zawiera szczegóły dostępu do kodu źródłowego za pośrednictwem Git.
- `Request` i `Analysis`: Określają strukturę zapytań analizy i ich odpowiedzi.
- `Preferences`: Zawiera preferencje analizy i progi dla różnych poziomów powagi i rodzajów problemów.

Ten plik jest niezbędny do definiowania struktury danych używanych w narzędziach do analizy kodu źródłowego i jest zaprojektowany tak, aby być wszechstronnym i elastycznym w obsłudze różnych aspektów oceny jakości kodu.

### v1/ast.proto
Plik `v1/ast.proto` definiuje strukturę reprezentującą drzewa składniowe (Abstract Syntax Trees - AST) w projekcie. Kluczowe komponenty tego pliku to:

- `Node`: Podstawowy element budulcowy AST. Każdy `Node` reprezentuje odrębny element drzewa składniowego, posiadający różne właściwości:
  - `Role`: Enumeracja kategoryzująca rolę węzła w AST, takie jak `ROOT`, `NAMESPACE`, `FUNCTION`, `CLASS` itp.
  - `Type`: Specyficzny dla języka typ węzła, kluczowy dla zrozumienia struktury kodu.
  - `Value`: Wartość węzła, używana głównie dla węzłów terminalnych, takich jak identyfikatory lub literały.
  - `Name`: Pełna kwalifikowana nazwa węzła, istotna głównie dla przestrzeni nazw lub funkcji.
  - `Filename`, `Start_line` i `End_line`: Dostarczają informacji o lokalizacji węzła w kodzie źródłowym.
  - `Children`: Lista węzłów potomnych, tworzących hierarchiczną strukturę AST.
  - `Nonduplicable`: Flaga wskazująca, czy węzeł może być rozpatrywany w kontekście wykrywania duplikacji.
  - `Metadata`: Dodatkowe dane powiązane z węzłem, zmienne w zależności od roli węzła.

Ten plik jest niezbędny dla aplikacji analizujących lub manipulujących AST kodu źródłowego, zapewniając elastyczną, a zarazem szczegółową strukturę do reprezentowania różnych elementów i ich relacji w składni języka programowania.

### v1/metadata.proto
Plik `v1/metadata.proto` zawiera protocol buffers dotyczące metadanych i różnych aspektów analizy oraz integracji kodu. Kluczowe komponenty to:

- `CodeLocation`: Reprezentuje precyzyjną lokalizację w kodzie (konkretną linię i kolumnę).
- `BugReport`: Opisuje raport błędu od różnych dostawców (jak Bugsnag). Zawiera szczegóły, takie jak klasa wyjątku, zrozumiały dla człowieka komunikat, URL raportu oraz dokładną lokalizację kodu, w której wystąpił problem.
- `CoverageData` i `CoverageReport`: Te komunikaty służą do reprezentowania danych o pokryciu testami. `CoverageReport` gromadzi dane dla określonego języka programowania, w tym procent kodu pokrytego testami oraz powiązany hash commitu.
- `PullRequest`: Opisuje pull request, w tym jego tytuł, URL, status (otwarty lub zamknięty) oraz szczegóły dotyczące gałęzi źródłowej i docelowej. Śledzi także, ile razy wiadomość związana z pull requestem została ponownie zakolejkowana, co może być ważne dla integracji z narzędziami takimi jak Sidekiq.

Te protocol buffers są niezbędne do integracji i zarządzania metadanymi związanymi z analizą kodu, śledzeniem błędów, pokryciem testów i obsługą pull requestów, zapewniając ustandaryzowany sposób obsługi takich danych na różnych platformach i narzędziach.

## Współpraca
Zapraszamy do współracy nad zawartością repozytorium! Jeśli masz pomysły na ulepszenia, dodatkowe funkcje lub poprawki, oto jak możesz pomóc:

### Przed rozpoczęciem
- Upewnij się, że Twoje zmiany są zgodne z ogólnym projektem i strukturą istniejących plików proto.
- Każdy plik `.proto` powinien być dobrze udokumentowany za pomocą znaczących komentarzy, które jasno wyjaśniają cel i sposób użycia każdej części struktury.

### Strategia tworzenia gałęzi
- W przypadku jakichkolwiek zmian utwórz nową gałąź od gałęzi `main`.
- Użyj opisowej nazwy dla swojej gałęzi, która odzwierciedla dokonywaną zmianę. Na przykład, `add-new-field-to-SourceFile` lub `fix-typo-in-Location`.

### Wprowadzanie zmian
- Dokonuj zmian w swojej gałęzi. Pamiętaj, aby utrzymać swój kod dobrze zorganizowany i skomentowany.
- Testuj swoje zmiany lokalnie, aby upewnić się, że działają zgodnie z oczekiwaniami i nie wprowadzają nowych problemów.

### Otwieranie pull requesta
- Gdy Twoje zmiany będą gotowe, wypchnij swoją gałąź do repozytorium.
- Utwórz żądanie pull request do gałęzi `main`.
- W opisie swojego pull requesta jasno opisz proponowane zmiany. Dołącz powody zmian i wszelkie dodatkowe konteksty, które mogą być pomocne dla recenzentów.
- Jeśli Twój pull request jest powiązany z jakimkolwiek otwartym problemem, odnieś się do tego problemu w swoim opisie.

### Proces przeglądu
- Opiekunowie repozytorium przejrzą Twój pull request i mogą zaproponować zmiany lub ulepszenia.
- Angażuj się w proces przeglądu, jeśli pojawią się komentarze lub dyskusje na temat Twojego pull requesta. Twoje zaangażowanie będzie kluczowe, aby Twoje zmiany zostały zintegrowane z gałęzią `main`.

### Scalanie
- Gdy Twój pull request zostanie zaakceptowany, jeden z opiekunów repozytorium scali je z gałęzią `main`.
- Po scaleniu Twoja gałąź może być bezpiecznie usunięta.

Bardzo cenimy wkład społeczności i uważamy, że może odgrywać kluczową rolę w rozwoju tego projektu. Czekamy na Twoje innowacyjne pomysły i współpracę!

## Licencja

Ten projekt jest objęty licencją MIT. Licencja MIT jest liberalną licencją oprogramowania, która nakłada ograniczone ograniczenia na ponowne użycie, udzielając pozwolenia na korzystanie, kopiowanie, modyfikowanie, łączenie, publikowanie, dystrybuowanie, udzielanie sublicencji i/lub sprzedaż kopii oprogramowania.

Aby uzyskać więcej szczegółów, proszę zapoznać się z plikiem [LICENSE](LICENSE) w tym repozytorium.

## Kontakt

W przypadku pytań, sugestii lub problemów dotyczących tego projektu, proszę korzystać ze strony [GitHub Issues](https://github.com/thecodebeat/ast-protos/issues). Jest to najszybszy sposób, aby uzyskać odpowiedź od opiekunów projektu i pozwala innym użytkownikom czerpać korzyści z dyskusji.

Jeśli masz konkretne zapytania lub potrzebujesz dyskusji, która nie mieści się w zakresie GitHub Issues, proszę użyć funkcji [GitHub Discussions](https://github.com/thecodebeat/ast-protos/discussions) dla tego repozytorium. Ta platforma zapewnia bardziej nieformalną przestrzeń do rozmów i zaangażowania społeczności.
