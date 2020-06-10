---
title: "C# 버전별 언어 기능"
date: "2020-06-10T19:45:00+09"
template: "post"
draft: false
slug: "/posts/csharp-features-by-version/"
category: "Tech"
tags:
  - "Tech"
  - "C#"
description: "C# 언어 버전별 기능 목록."
---

| | |
| -- | -- |
| C# 1 | Classes<br>Structs<br>Interfaces<br>Events<br>Properties<br>Delegates<br>Expressions<br>Statements<br>Attributes |
| C# 2 | Generics<br>Nullable value types<br>Method group conversions<br>Anonymous methods<br>Delegate covariance and contravariance<br>Iterators (`yield return`)<br>Partial types<br>Static classes<br>Separate getter/setter access on properties<br>Namespace alias qualifier `::` syntax<br>The `global` **namespace alias<br>Extern aliases<br>Fixed-size buffers<br>`InternalsVisibleToAttribute` support |
| C# 3 | Partial methods<br>Automatically implemented properties<br>Implicitly typed local variables (`var`)<br>Implicitly typed arrays (`new[]`)<br>Object initializers<br>Collection initializers<br>Anonymous types<br>Lambda expressions (delegates)<br>Lambda expressions (expression trees)<br>Extension methods<br>Query expressions|
| C# 4 | Dynamic typing<br>Optional parameters<br>Named arguments<br>Linked primary interop assemblies<br>Special rules for optional parameters in COM<br>Access to named indexers (COM only)<br>Generic variance for interfaces and delegates<br>Implementation change to lock statements<br>Implementation changes to field-like events<br>Field-like event access within the declaring class |
| C# 5 | `async` / `await`<br>Changes to `foreach` iteration variable capture<br>Caller information attributes |
| C# 6 | Read-only automatically implemented properties<br>Initializers for automatically implemented properties<br>Remove requirement to call `this()` in constructors for structs containing automatically implemented properties<br>Expression-bodied members<br>Interpolated string literals<br>The `nameof` operator<br>The `using static` directive<br>Object initializers using indexers<br>Collection initializers using extension Add methods<br>The null conditional `?.` operator<br>Exception filters<br>Removed restrictions on awaiting in `try/catch`, `try/finally`, and `try/catch` statements |
| C# 7.0 | Tuples<br>Deconstruction via `Deconstruct` methods<br>Initial patterns: constant patterns, type patterns, `var` **patterns<br>Use of patterns with the `is` **operator<br>Use of patterns in switch statements, including guard clauses (`when`)<br>Ref locals<br>Ref return<br>Binary integer literals<br>Underscore separators in numeric literals<br>Returning custom task types from async methods<br>More kinds of expression-bodied members |
| C# 7.1 | The `default` **literal<br>Improvements to type patterns matching against generic values<br>Async entry points (`async Task Main`)<br>Inferred tuple element names |
| C# 7.2 | Allow the conditional `?:` operator to work with *ref*<br>`ref readonly` locals and return types<br>`in` parameters<br>Read-only structs<br>Extension methods with *ref/in* parameters<br>Ref-like structs<br>`stackalloc`  support for `Span<T>`<br>Nontrailing named arguments<br>The `private protected` access modifier<br>Underscore separators in numeric literals directly after the `0x` or `0b` base specifier|
| C# 7.3 | Access to fixed-sized buffers via fields without *fixed* statements<br>`*==*` and `!=` operators for tuples<br>Use of pattern and `out` variables in field, property, and constructor initializers<br>Reassignment of ref locals<br>Initializers in `stackalloc` statements<br>Pattern-based fixed statements using `GetPinnableReference`<br>Generic type constraints now permitted on `Enum` and `Delegate`<br>New generic type constraint of `unmanaged`<br>Placement of attributes of fields backing automatically implemented properties|
| C# 8.0 | Readonly members<br>Default interface methods<br>Pattern matching enhancements: Switch expressions, Property patterns, Tuple patterns Positional patterns<br>Using declarations<br>Static local functions<br>Disposable ref structs<br>Nullable reference types<br>Asynchronous streams<br>Indices and ranges<br>Null-coalescing assignment<br>Unmanaged constructed types<br>`stackalloc` in nested expressions<br>Enhancement of interpolated verbatim string |
| C# 9.0<br>(preview) | Init-only properties<br>- Init accessors and readonly fields<br>Records (`data class`)<br>- With-expressions<br>- Value-based equality<br>- Data members<br>- Positional records<br>- With-expressions and inheritance<br>- Value-based equality and inheritance<br>Top-level programs (omitting `Main` method)<br>Improved pattern matching<br>- Simple type patterns<br>- Relational patterns<br>- Logical patterns<br>- Target-typed `new` expressions<br>- Target typed `??` and `?:`<br>Covariant returns|

# 참고
- C# in Depth 4 ed
- The history of C# https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-version-history
- Welcome to C# 9.0 https://devblogs.microsoft.com/dotnet/welcome-to-c-9-0/
- dotnet/csharplang Milestone: 9.0 candidate https://github.com/dotnet/csharplang/milestone/15
