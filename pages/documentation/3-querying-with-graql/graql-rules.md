---
title: Graql Rules
keywords: graql, reasoner
last_updated: January 2017
tags: [graql, reasoning]
summary: "Graql Rules"
sidebar: documentation_sidebar
permalink: /documentation/graql/graql-rules.html
folder: documentation
---

## Rule Objects
Grakn supports Graql-native, rule-based reasoning to allow automated capture and evolution of patterns within the graph. Graql reasoning is performed at query time and is guaranteed to be complete.

The rule objects are instances of inference rule RuleType and assume the following general form:

```
if [rule-body] then [rule-head]
```
or in Prolog/Datalog terms:

```
[rule-head] :- [rule-body].
```

In logical terms, we restrict the rules to be definite Horn clauses (i.e. disjunctions of atoms with at most one unnegated atom). In our system we define both the head and the body of rules as Graql patterns. Consequently, the rules are statements of the form:

```
p :- q1, q2, ..., qn
```

where p and q's are atoms that each correspond to a single Graql pattern.

## Graql Rule Syntax
In Graql we refer to the body of the rule as the left-hand-side of the rule and the head as the right-hand-side of the rule. Therefore in Graql terms we define rule objects in the following way:

```graql
$optional-name isa inference-rule,
lhs {
    ...;
    ...;
    ...;
},
rhs {
    ...;
};
```

In Graql the left-hand-side of the rule is required to be a conjunctive pattern, whereas the right-hand-side should contain a single pattern.

A classic reasoning example is the ancestor example: the two Graql rules R1 and R2 stated below define the ancestor relationship which can be understood as either happening between two generations directly between a parent and a child or between three generations when the first generation hop is expressed via a parentship relation and the second generation hop is captured by an ancestor relation.

```graql
$R1 isa inference-rule,
lhs {
    (parent: $p, child: $c) isa Parent;
},
rhs {
    (ancestor: $p, descendant: $c) isa Ancestor;
};

$R2 isa inference-rule,
lhs {
    (parent: $p, child: $c) isa Parent;
    (ancestor: $c, descendant: $d) isa Ancestor;
},
rhs {
    (ancestor: $p, descendant: $d) isa Ancestor;
};
```

When adding rules such as those defined above with Graql, we simply use an `insert` statement, and load the rules, saved as a *.gql* file, into the graph in a standard manner, much as for an ontology. 

The above defined rules correspond to the following definition of Prolog/Datalog clauses:

```
R1: ancestor(X, Y) :- parent(X, Y)  
R2: ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y)
```


## Allowed Graql Constructs in Rules
The tables below summarise Graql constructs that are allowed to appear in LHS
and RHS of rules.   

### Queries

| Description        | LHS | RHS
| -------------------- |:--|:--|
| atomic queries | ✓ | ✓ |
| conjunctive queries        | ✓ | x |
| disjunctive queries        | x | x |  

### Variable Patterns

| Description        | Pattern Example           | LHS | RHS
| -------------------- |:--- |:--|:--|
| `isa` | `$x isa person;` | ✓ | x |
| `id`  | `$x id "264597";` | ✓ | indirect only  |
| `value` | `$x value contains "Bar";`  | ✓ | indirect only  |
| `has` | `$x has age < 20;` | ✓ | ✓ |
| `relation` | `(parent: $x, child: $y) isa parentship;` | ✓ | ✓ |
| resource comparison | `$x value > $y;`  | ✓ | x |
| `!=` | `$x != $y;` | ✓ | x |
| `has-scope` | `($x, $y) has-scope $z;$x has-scope $y;`  | ✓ | x |

### Type Properties

| Description        | Pattern Example   | LHS | RHS
| -------------------- |:---|:--|:--|
| `sub`        | `$x sub type;` | ✓| x |
| `plays-role` | `$x plays-role parent;` |✓| x |
| `has-resource`        | `$x has-resource firsname;` | ✓ | x |  
| `has-role`   | `marriage has-role $x;` | ✓ | x |
| `is-abstract` | `$x is-abstract;` | ✓ | x |
| `datatype` | `$x isa resource, datatype string;` | ✓| x |
| `regex` | `$x isa resource, regex /hello/;` | ✓ | x |

## Configuration options
Graql offers certain degrees of freedom in deciding how and if reasoning should be performed. Namely it offers two options:

* **whether reasoning should be on**. This option is self-explanatory. If the reasoning is not turned on, the rules will not be triggered and no knowledge will be inferred. 
* **whether inferred knowledge should be materialised (persisted to the graph) or stored in memory**. Persisting to graph has a huge impact on performance when compared to in-memory inference, and, for larger graphs, materialisation should either be avoided or queries be limited by employing the _limit_ modifier, which allows termination in sensible time.


## Comments
Want to leave a comment? Visit <a href="https://github.com/graknlabs/docs/issues/42" target="_blank">the issues on Github for this page</a> (you'll need a GitHub account). You are also welcome to contribute to our documentation directly via the "Edit me" button at the top of the page.

{% include links.html %}