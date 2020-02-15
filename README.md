apex-parser
===========

Parser for Salesforce Apex Language. This is based on a ANTLR4 grammar (see antlr/ApexParser.g4) using antlr4ts to generate a parser/lexer in Typescript. The grammar has been extensively used for parsing with Java but not with antlr4ts.

This module just contains the Parser & Lexer and provides no further support for analysing the generated parse trees beyond what
is provided by antlr4ts. 

As Apex is a case-insenstive language you need to use the provided CaseInsensitiveInputStream for the parser to function correctly. You can find some minimal examples in the src/\__test__ directory. Supports parsing of class & trigger files but not anonymous code snippets.

### Example
To parse a class file:

    let lexer = new ApexLexer(new CaseInsensitiveInputStream("public class Hello {}"))
    let tokens  = new CommonTokenStream(lexer);

    let parser = new ApexParser(tokens)
    let context = parser.compilationUnit()

The 'context' is a CompilationUnitContext object which is the root of the parsed representation of the class. You can access the parse tree via functions on it.

### Change grammar
If you change the Parser or Lexer grammar files you will need to update the parser with

    npm run antlr4ts 

### History
    2.0.0 - Supports trigger parsing and switch statement parsing syntax was corrected
    1.0.0 - Initial version

### Source & Licenses

All the source code included uses a 3-clause BSD license. The only third-party component included is the Apex Antlr4 grammar originally from [Tooling-force.com](https://github.com/neowit/tooling-force.com), although this version used is now markedly different from the original.  
