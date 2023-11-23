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

## Contributing
We welcome contributions to our `.proto` files! If you have ideas for improvements, additional features, or corrections, here's how you can contribute:

### Before You Start
- Make sure your changes are consistent with the overall design and structure of the existing proto files.
- Each `.proto` file should be well-documented with meaningful comments that clearly explain the purpose and usage of each part of the structure.

### Branching Strategy
- For any changes, please create a new branch from the `main` branch. 
- Use a descriptive name for your branch that reflects the change you're making. For example, `add-new-field-to-SourceFile` or `fix-typo-in-Location`.

### Making Changes
- Make your changes in your branch. Be sure to keep your code well-organized and commented.
- Test your changes locally to ensure they are working as expected and do not introduce any new issues.

### Submitting a Pull Request
- Once your changes are ready, push your branch to the repository.
- Create a pull request against the `main` branch.
- In your pull request description, clearly describe the changes you are proposing. Include the reasons for the changes and any additional context that might be helpful for reviewers.
- If your pull request is related to any open issue, reference that issue in your description.

### Review Process
- The maintainers will review your pull request and may suggest changes or improvements.
- Engage in the review process if there are comments or discussions about your pull request. Your involvement will be crucial in getting your changes integrated.

### Merging
- Once your pull request is approved, one of the maintainers will merge it into the `main` branch.
- After merging, your branch can be safely deleted.

Your contributions are greatly appreciated and play a vital role in the improvement of this project. We look forward to your innovative ideas and collaboration!

## Licencja

Ten projekt jest objęty licencją MIT. Licencja MIT jest liberalną licencją oprogramowania, która nakłada ograniczone ograniczenia na ponowne użycie, udzielając pozwolenia na korzystanie, kopiowanie, modyfikowanie, łączenie, publikowanie, dystrybuowanie, udzielanie sublicencji i/lub sprzedaż kopii oprogramowania.

Aby uzyskać więcej szczegółów, proszę zapoznać się z plikiem [LICENSE](LICENSE) w tym repozytorium.

## Contact

For questions, suggestions, or issues regarding this project, please use the [GitHub Issues](https://github.com/thecodebeat/ast-protos/issues) page. This is the fastest way to get a response from the project maintainers and allows other users to benefit from the discussion.

If you have specific queries or require discussion that doesn't fit within the scope of GitHub Issues, please use the [GitHub Discussions](https://github.com/thecodebeat/ast-protos/discussions) feature for this repository. This platform provides a more informal space for conversation and community engagement.