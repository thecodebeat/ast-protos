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

## License

This project is licensed under the MIT License. The MIT License is a permissive free software license that provides limited restriction on reuse, granting permission to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software.

For more details, please see the [LICENSE](LICENSE) file in this repository.

## Contact

For questions, suggestions, or issues regarding this project, please use the [GitHub Issues](https://github.com/thecodebeat/ast-protos/issues) page. This is the fastest way to get a response from the project maintainers and allows other users to benefit from the discussion.

If you have specific queries or require discussion that doesn't fit within the scope of GitHub Issues, please use the [GitHub Discussions](https://github.com/thecodebeat/ast-protos/discussions) feature for this repository. This platform provides a more informal space for conversation and community engagement.
