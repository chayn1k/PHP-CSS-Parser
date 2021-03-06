# Revision History

## 5.0

### 5.0.0 (2013-03-20)

* Correctly parse all known CSS 3 units (including Hz and kHz).
* Output RGB colors in short (#aaa or #ababab) notation
* Be case-insensitive when parsing identifiers.
* *No deprecations*

#### Backwards-incompatible changes

* `Sabberworm\CSS\Value\Color`’s `__toString` method overrides `CSSList`’s to maybe return something other than `type(value, …)` (see above).

### 5.0.1 (2013-03-20)

* Internal cleanup
* *No backwards-incompatible changes*
* *No deprecations*

### 5.0.2 (2013-03-21)

* CHANGELOG.md file added to distribution
* *No backwards-incompatible changes*
* *No deprecations*

## 4.0

### 4.0.0 (2013-03-19)

* Support for more @-rules
* Generic interface `Sabberworm\CSS\Property\AtRule`, implemented by all @-rule classes
* *No deprecations*

#### Backwards-incompatible changes

* `Sabberworm\CSS\RuleSet\AtRule` renamed to `Sabberworm\CSS\RuleSet\AtRuleSet`
* `Sabberworm\CSS\CSSList\MediaQuery` renamed to `Sabberworm\CSS\RuleSet\CSSList\AtRuleBlockList` with differing semantics and API (which also works for other block-list-based @-rules like `@supports`).

## 3.0

### 3.0.0 (2013-03-06)

* Support for lenient parsing (on by default)
* *No deprecations*

#### Backwards-incompatible changes

* All properties (like whether or not to use `mb_`-functions, which default charset to use and – new – whether or not to be forgiving when parsing) are now encapsulated in an instance of `Sabberworm\CSS\Settings` which can be passed as the second argument to `Sabberworm\CSS\Parser->__construct()`.
* Specifying a charset as the second argument to `Sabberworm\CSS\Parser->__construct()` is no longer supported. Use `Sabberworm\CSS\Settings::create()->withDefaultCharset('some-charset')` instead.
* Setting `Sabberworm\CSS\Parser->bUseMbFunctions` has no effect. Use `Sabberworm\CSS\Settings::create()->withMultibyteSupport(true/false)` instead.
* `Sabberworm\CSS\Parser->parse()` may throw a `Sabberworm\CSS\Parsing\UnexpectedTokenException` when in strict parsing mode.

## 2.0

### 2.0.0 (2013-01-29)

* Allow multiple rules of the same type per rule set

#### Backwards-incompatible changes

* `Sabberworm\CSS\RuleSet->getRules()` returns an index-based array instead of an associative array. Use `Sabberworm\CSS\RuleSet->getRulesAssoc()` (which eliminates duplicate rules and lets the later rule of the same name win).
* `Sabberworm\CSS\RuleSet->removeRule()` works as it did before except when passed an instance of `Sabberworm\CSS\Rule\Rule`, in which case it would only remove the exact rule given instead of all the rules of the same type. To get the old behaviour, use `Sabberworm\CSS\RuleSet->removeRule($oRule->getRule()`;

## 1.0

Initial release of a stable public API.

## 0.9

Last version not to use PSR-0 project organization semantics.