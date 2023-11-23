# Codebeat Abstract Syntax Tree Protocol Buffers

*Read this in other languages: [Polski](README.pl.md)*

## Introduction

![European Funds](assets/en/FE_IR_rgb-1.jpg "European Funds")

Code quest sp. z o.o. company, in the years 2017-2020, carried out a research and development project numbered POIR.01.01.01-00-0792/16 under the [Smart Growth Operational Programme 2014-2020]((https://www.funduszeeuropejskie.gov.pl/strony/o-funduszach/dokumenty/program-inteligentny-rozwoj-dokument/)) of the National Centre for Research and Development. The project was titled "Codebeat - the use of artificial intelligence in a static analysis of software quality". The subject of the project was industrial research in the field of using artificial intelligence for static software quality analysis, as well as the development of an innovative set of metrics and heuristics for new object-oriented and functional languages. Before the commencement of the project, codequest sp. z o.o. committed to disseminating the results of the research and development work, among others, in the form of free or open source software stored in a publicly accessible place. The files in this repository are the result of the development works. They contain the definitions of the structures abstracting syntax trees (AST) which represent the grammars of specific programming languages, and also the structures crucial for computation of quality metrics.

## Project Overview
Welcome to the repository of Codebeat, a comprehensive solution for static analysis of source code across multiple programming languages. This repository is specifically dedicated to the protocol buffer (proto) files that form the backbone of our static analysis Software as a Service (SaaS).

Our service provides an in-depth analysis of source code, identifying potential issues, code duplications, and providing insights into the overall quality and structure of the codebase. The proto files in this repository define the data structures used for representing and communicating analysis results, code metadata, and other crucial information processed by our service.

The `.proto` files are exposed here for several purposes:

- **Interoperability**: By sharing these definitions, in the future, we will enable other services and tools to integrate seamlessly with our analysis platform, ensuring compatibility and ease of data exchange.
- **Transparency**: We believe in the importance of transparency in tooling used for software development. By making these proto files public, we offer insights into how data is structured and handled in our analyses.
- **Community Collaboration**: We encourage contributions and feedback from the developer community. By understanding the structure of our data, developers can suggest improvements, extensions, or even new use cases.

In this repository, you will find the following proto files:
- `v1/analyser.proto`: Defines structures for analyzing and reporting on the source code, such as issue detection and code quality metrics.
- `v1/ast.proto`: Contains definitions related to Abstract Syntax Trees (ASTs), crucial for understanding the syntactic structure of the analyzed code.
- `v1/metadata.proto`: Encompasses various metadata structures like bug reports, code coverage data, and pull request information.

Please note that these files are part of a larger private codebase powering our SaaS. The accompanying server-side and client-side implementation code is not publicly available as it forms the core of our proprietary analysis engine.

We invite you to explore these proto files, integrate them into your workflows, and contribute to the continuous improvement of static code analysis. Your feedback and contributions are invaluable to us.

## Getting Started

This section provides guidance on how to use the protocol buffer files available in this repository. These files are crucial for understanding and utilizing the data structures used in our static analysis SaaS.

### Prerequisites

Before you begin, ensure you have the following installed:

- Protocol Buffers (ProtoBuf): You need to have the Protocol Buffers compiler (`protoc`) installed to generate data access classes in your preferred language from these `.proto` files.
- A compatible programming environment: Ensure your development environment supports the language you plan to use for interacting with these proto files.

### Steps to Use

1. **Clone the Repository**:
   Begin by cloning this repository to your local machine. Use the following command:

	```bash
	git clone [repository-url]
	```
	
	Replace `[repository-url]` with the actual URL of this repository.

2. **Install Protocol Buffers Compiler**:
If you haven't already, install the Protocol Buffers compiler. Instructions can be found on the [Protocol Buffers GitHub page](https://github.com/protocolbuffers/protobuf).

3. **Generate Language-Specific Code**:
Navigate to the directory containing the `.proto` files and run the Protocol Buffers compiler to generate code in your desired language. For example:

	```bash
	protoc --java_out=./java_gen v1/*.proto
	```

	This command generates Java code for all proto files in the `v1` directory. Replace `--java_out` with the appropriate option for your language.

4. **Integrate Generated Code into Your Project**:
Move the generated code to your project's source directory. Make sure to resolve any dependencies or import paths as required by your project's structure.

5. **Usage Examples**:
After integrating the generated code, you can create, manipulate, and interact with the data structures defined in the proto files. Example usage might include creating a new `Issue` object, populating fields from analysis results, and serializing it for storage or transmission.

### Further Assistance

For more detailed instructions on using Protocol Buffers, please refer to the [official documentation](https://protobuf.dev/overview/). Should you encounter any issues or have specific use cases, please feel free to open an issue in this repository for support.

## Contents
- `v1/analyser.proto`: This file defines structures for source code analysis, including issue detection, code quality metrics, and analysis reporting.
- `v1/ast.proto`: Contains definitions for representing Abstract Syntax Trees (ASTs), essential for understanding and analyzing the syntactic structure of the code.
- `v1/metadata.proto`: Encompasses structures for metadata related to code analysis, including bug reports, test coverage data, and pull request details.

## Detailed Descriptions

### v1/analyser.proto
The `v1/analyser.proto` file defines a set of protocol buffers used for analyzing source code within a project. The primary structures and their purposes are as follows:

- `SourceFile`: Represents a source file in the project, including its path, content hash, actual content, and validity status.
- `SupportingFile`: Defines a supporting file which is useful for analysis but not intended to be parsed.
- `Location` and `ExactLocation`: Provide locations for various entities within a source file, with `ExactLocation` offering more precise positioning (like start and end lines).
- `Severity`: An enumeration that represents the seriousness of an issue or similarity, ranging from `NONE` to `CRITICAL`.
- `Issue` and `Similarity`: Define problems within the code, where `Similarity` focuses on issues involving code duplication.
- `LintIssue` and `LintResult`: Used for representing issues identified by linters and their results.
- `BrakemanIssue` and `BrakemanResult`: Specific structures for issues identified by the Brakeman analysis tool.
- `GenericIssue`: Describes problems reported by experimental metrics.
- `Namespace`: Represents a namespace in the code, including metrics, functions, and issues associated with it.
- `Report`: Aggregates the analysis results, including namespaces, source files, supporting files, and various types of issues.
- `Error`: Details errors that might occur during analysis, including their types and debug information.
- `Timestamps`: Captures various timestamps related to the analysis process.
- `GitDetails`: Contains details for accessing source code via Git.
- `Request` and `Analysis`: Define the structure for analysis requests and their responses.
- `Preferences`: Holds analysis preferences and thresholds for various severities and issue types.

This file is integral for defining the structure of data used in source code analysis tools and is designed to be comprehensive and flexible for handling different aspects of code quality assessment.

### v1/ast.proto
The `v1/ast.proto` file defines the structure for representing Abstract Syntax Trees (ASTs) in your project. The key components of this file include:

- `Node`: The fundamental building block of the AST. Each `Node` represents a distinct element in the syntax tree, with various properties:
  - `Role`: An enumeration that categorizes the role of the node in the AST, such as `ROOT`, `NAMESPACE`, `FUNCTION`, `CLASS`, etc.
  - `Type`: A language-specific type for the node, crucial for understanding the code structure.
  - `Value`: The value of the node, used primarily for terminal nodes like identifiers or literals.
  - `Name`: The fully qualified name of the node, relevant mainly for namespaces or functions.
  - `Filename`, `Start_line`, and `End_line`: Provide location information for the node within the source code.
  - `Children`: A list of child nodes, building the hierarchical structure of the AST.
  - `Nonduplicable`: A flag indicating whether the node can be considered for duplication detection.
  - `Metadata`: Additional data associated with the node, varying based on the node's role.

This file is essential for applications that analyze or manipulate source code ASTs, providing a flexible yet detailed structure for representing various elements and their relationships in a programming language's syntax.

### v1/metadata.proto
The `v1/metadata.proto` file contains protocol buffers that focus on metadata and various aspects of code analysis and integration. Key components include:

- `CodeLocation`: Represents a precise location in the code (a specific line and column).
- `BugReport`: Describes a bug report from various providers (like Bugsnag). It includes details like the exception class, human-readable message, URL of the report, and the exact code location where the problem occurred.
- `CoverageData` and `CoverageReport`: These messages are used to represent test coverage data. `CoverageReport` gathers data for a specific programming language, including the percentage of code covered by tests and the associated commit hash.
- `PullRequest`: Describes a pull request, including its title, URL, status (open or closed), and details about the source and destination branches. It also tracks the number of times a message related to the pull request was requeued, which can be important for integration with tools like Sidekiq.

These protocol buffers are essential for integrating and managing metadata related to code analysis, bug tracking, test coverage, and pull request handling, providing a standardized way to handle such data across different platforms and tools.

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

## License

This project is licensed under the MIT License. The MIT License is a permissive free software license that provides limited restriction on reuse, granting permission to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software.

For more details, please see the [LICENSE](LICENSE) file in this repository.

## Kontakt

W przypadku pytań, sugestii lub problemów dotyczących tego projektu, proszę korzystać ze strony [GitHub Issues](https://github.com/thecodebeat/ast-protos/issues). Jest to najszybszy sposób, aby uzyskać odpowiedź od opiekunów projektu i pozwala innym użytkownikom czerpać korzyści z dyskusji.

Jeśli masz konkretne zapytania lub potrzebujesz dyskusji, która nie mieści się w zakresie GitHub Issues, proszę użyć funkcji [GitHub Discussions](https://github.com/thecodebeat/ast-protos/discussions) dla tego repozytorium. Ta platforma zapewnia bardziej nieformalną przestrzeń do rozmów i zaangażowania społeczności.
