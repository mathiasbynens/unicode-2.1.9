# Unicode v2.1.9 data

JavaScript-compatible Unicode data for use in Node.js. Included: arrays of code points, arrays of symbols, and regular expressions for Unicode v2.1.9’s categories, scripts, script extensions, blocks, and properties, as well as bidi mirroring and case folding data.

The data files in this module are generated as part of the [node-unicode-data](https://mths.be/node-unicode-data) project. **Please report any bugs or requests [in the appropriate issue tracker](https://github.com/mathiasbynens/node-unicode-data/issues).**

## Installation

```bash
npm install unicode-2.1.9 --save-dev
```

**Note:** _unicode-2.1.9_ is supposed to be used in build scripts (i.e. as a `devDependency`), and not at runtime (i.e. as a regular `dependency`).

## Regular expressions

The Unicode data modules ship with pre-compiled regular expressions for categories, scripts, script extensions, blocks, and properties. But maybe you want to create a single regular expression that combines several categories, scripts, etc. In that case, [***you should use Regenerate***](https://mths.be/regenerate). For example, to construct a regex that matches all symbols in the Arabic and Greek scripts as per Unicode v6.3.0:

```js
const regenerate = require('regenerate');
const set = regenerate()
	.add(require('unicode-6.3.0/script-extensions/Arabic/code-points')) // or `…/symbols`, doesn’t matter
	.add(require('unicode-6.3.0/script-extensions/Greek/code-points')); // or `…/symbols`, doesn’t matter
console.log(set.toString());
// Then you might want to use a template like this to write the result to a file, along with any regex flags you might need:
// const regex = /<%= set.toString() %>/gim;
```

## Usage

```js
// Get an array of code points in a given Unicode category:
const codePoints = require('unicode-2.1.9/categories/Lu/code-points');
// Get an array of symbols (strings) in a given Unicode category:
const symbols = require('unicode-2.1.9/categories/Lu/symbols');
// Get a regular expression that matches any symbol in a given Unicode category:
const regex = require('unicode-2.1.9/categories/Lu/regex');
// Get the canonical category a given code point belongs to:
// (Note: U+0041 is LATIN CAPITAL LETTER A)
const category = require('unicode-2.1.9/categories')[ 0x41 ];
// Get an array of all code points with `Bidi_Class=Other_Neutral`:
const on = require('unicode-2.1.9/bidi-classes/Other_Neutral/code-points');
// Get a map from code points to bidi classes:
const bidiClassMap = require('unicode-2.1.9/bidi-classes');
// Get the directionality of a given code point:
const directionality = require('unicode-2.1.9/bidi-classes').get(0x41);

// …you get the idea.
```

Other than categories, data on Unicode properties, blocks, scripts, and script extensions is available too (for recent versions of the Unicode standard). Here’s the full list of the available data for v2.1.9:

```js
// properties:

require('unicode-2.1.9/properties/ASCII/code-points');
require('unicode-2.1.9/properties/ASCII/symbols');
require('unicode-2.1.9/properties/ASCII/regex');

require('unicode-2.1.9/properties/Any/code-points');
require('unicode-2.1.9/properties/Any/symbols');
require('unicode-2.1.9/properties/Any/regex');

require('unicode-2.1.9/properties/Assigned/code-points');
require('unicode-2.1.9/properties/Assigned/symbols');
require('unicode-2.1.9/properties/Assigned/regex');

require('unicode-2.1.9/properties/Bidi_Mirrored/code-points');
require('unicode-2.1.9/properties/Bidi_Mirrored/symbols');
require('unicode-2.1.9/properties/Bidi_Mirrored/regex');

// categories:

require('unicode-2.1.9/categories').get(codePoint); // lookup map

require('unicode-2.1.9/categories/Cased_Letter/code-points');
require('unicode-2.1.9/categories/Cased_Letter/symbols');
require('unicode-2.1.9/categories/Cased_Letter/regex');

require('unicode-2.1.9/categories/Close_Punctuation/code-points');
require('unicode-2.1.9/categories/Close_Punctuation/symbols');
require('unicode-2.1.9/categories/Close_Punctuation/regex');

require('unicode-2.1.9/categories/Connector_Punctuation/code-points');
require('unicode-2.1.9/categories/Connector_Punctuation/symbols');
require('unicode-2.1.9/categories/Connector_Punctuation/regex');

require('unicode-2.1.9/categories/Control/code-points');
require('unicode-2.1.9/categories/Control/symbols');
require('unicode-2.1.9/categories/Control/regex');

require('unicode-2.1.9/categories/Currency_Symbol/code-points');
require('unicode-2.1.9/categories/Currency_Symbol/symbols');
require('unicode-2.1.9/categories/Currency_Symbol/regex');

require('unicode-2.1.9/categories/Dash_Punctuation/code-points');
require('unicode-2.1.9/categories/Dash_Punctuation/symbols');
require('unicode-2.1.9/categories/Dash_Punctuation/regex');

require('unicode-2.1.9/categories/Decimal_Number/code-points');
require('unicode-2.1.9/categories/Decimal_Number/symbols');
require('unicode-2.1.9/categories/Decimal_Number/regex');

require('unicode-2.1.9/categories/Enclosing_Mark/code-points');
require('unicode-2.1.9/categories/Enclosing_Mark/symbols');
require('unicode-2.1.9/categories/Enclosing_Mark/regex');

require('unicode-2.1.9/categories/Final_Punctuation/code-points');
require('unicode-2.1.9/categories/Final_Punctuation/symbols');
require('unicode-2.1.9/categories/Final_Punctuation/regex');

require('unicode-2.1.9/categories/Format/code-points');
require('unicode-2.1.9/categories/Format/symbols');
require('unicode-2.1.9/categories/Format/regex');

require('unicode-2.1.9/categories/Initial_Punctuation/code-points');
require('unicode-2.1.9/categories/Initial_Punctuation/symbols');
require('unicode-2.1.9/categories/Initial_Punctuation/regex');

require('unicode-2.1.9/categories/Letter/code-points');
require('unicode-2.1.9/categories/Letter/symbols');
require('unicode-2.1.9/categories/Letter/regex');

require('unicode-2.1.9/categories/Letter_Number/code-points');
require('unicode-2.1.9/categories/Letter_Number/symbols');
require('unicode-2.1.9/categories/Letter_Number/regex');

require('unicode-2.1.9/categories/Line_Separator/code-points');
require('unicode-2.1.9/categories/Line_Separator/symbols');
require('unicode-2.1.9/categories/Line_Separator/regex');

require('unicode-2.1.9/categories/Lowercase_Letter/code-points');
require('unicode-2.1.9/categories/Lowercase_Letter/symbols');
require('unicode-2.1.9/categories/Lowercase_Letter/regex');

require('unicode-2.1.9/categories/Mark/code-points');
require('unicode-2.1.9/categories/Mark/symbols');
require('unicode-2.1.9/categories/Mark/regex');

require('unicode-2.1.9/categories/Math_Symbol/code-points');
require('unicode-2.1.9/categories/Math_Symbol/symbols');
require('unicode-2.1.9/categories/Math_Symbol/regex');

require('unicode-2.1.9/categories/Modifier_Letter/code-points');
require('unicode-2.1.9/categories/Modifier_Letter/symbols');
require('unicode-2.1.9/categories/Modifier_Letter/regex');

require('unicode-2.1.9/categories/Modifier_Symbol/code-points');
require('unicode-2.1.9/categories/Modifier_Symbol/symbols');
require('unicode-2.1.9/categories/Modifier_Symbol/regex');

require('unicode-2.1.9/categories/Nonspacing_Mark/code-points');
require('unicode-2.1.9/categories/Nonspacing_Mark/symbols');
require('unicode-2.1.9/categories/Nonspacing_Mark/regex');

require('unicode-2.1.9/categories/Number/code-points');
require('unicode-2.1.9/categories/Number/symbols');
require('unicode-2.1.9/categories/Number/regex');

require('unicode-2.1.9/categories/Open_Punctuation/code-points');
require('unicode-2.1.9/categories/Open_Punctuation/symbols');
require('unicode-2.1.9/categories/Open_Punctuation/regex');

require('unicode-2.1.9/categories/Other/code-points');
require('unicode-2.1.9/categories/Other/symbols');
require('unicode-2.1.9/categories/Other/regex');

require('unicode-2.1.9/categories/Other_Letter/code-points');
require('unicode-2.1.9/categories/Other_Letter/symbols');
require('unicode-2.1.9/categories/Other_Letter/regex');

require('unicode-2.1.9/categories/Other_Number/code-points');
require('unicode-2.1.9/categories/Other_Number/symbols');
require('unicode-2.1.9/categories/Other_Number/regex');

require('unicode-2.1.9/categories/Other_Punctuation/code-points');
require('unicode-2.1.9/categories/Other_Punctuation/symbols');
require('unicode-2.1.9/categories/Other_Punctuation/regex');

require('unicode-2.1.9/categories/Other_Symbol/code-points');
require('unicode-2.1.9/categories/Other_Symbol/symbols');
require('unicode-2.1.9/categories/Other_Symbol/regex');

require('unicode-2.1.9/categories/Paragraph_Separator/code-points');
require('unicode-2.1.9/categories/Paragraph_Separator/symbols');
require('unicode-2.1.9/categories/Paragraph_Separator/regex');

require('unicode-2.1.9/categories/Private_Use/code-points');
require('unicode-2.1.9/categories/Private_Use/symbols');
require('unicode-2.1.9/categories/Private_Use/regex');

require('unicode-2.1.9/categories/Punctuation/code-points');
require('unicode-2.1.9/categories/Punctuation/symbols');
require('unicode-2.1.9/categories/Punctuation/regex');

require('unicode-2.1.9/categories/Separator/code-points');
require('unicode-2.1.9/categories/Separator/symbols');
require('unicode-2.1.9/categories/Separator/regex');

require('unicode-2.1.9/categories/Space_Separator/code-points');
require('unicode-2.1.9/categories/Space_Separator/symbols');
require('unicode-2.1.9/categories/Space_Separator/regex');

require('unicode-2.1.9/categories/Spacing_Mark/code-points');
require('unicode-2.1.9/categories/Spacing_Mark/symbols');
require('unicode-2.1.9/categories/Spacing_Mark/regex');

require('unicode-2.1.9/categories/Surrogate/code-points');
require('unicode-2.1.9/categories/Surrogate/symbols');
require('unicode-2.1.9/categories/Surrogate/regex');

require('unicode-2.1.9/categories/Symbol/code-points');
require('unicode-2.1.9/categories/Symbol/symbols');
require('unicode-2.1.9/categories/Symbol/regex');

require('unicode-2.1.9/categories/Titlecase_Letter/code-points');
require('unicode-2.1.9/categories/Titlecase_Letter/symbols');
require('unicode-2.1.9/categories/Titlecase_Letter/regex');

require('unicode-2.1.9/categories/Unassigned/code-points');
require('unicode-2.1.9/categories/Unassigned/symbols');
require('unicode-2.1.9/categories/Unassigned/regex');

require('unicode-2.1.9/categories/Uppercase_Letter/code-points');
require('unicode-2.1.9/categories/Uppercase_Letter/symbols');
require('unicode-2.1.9/categories/Uppercase_Letter/regex');

// bidi classes:

require('unicode-2.1.9/bidi-classes').get(codePoint); // lookup map

require('unicode-2.1.9/bidi-classes/Arabic_Number/code-points');
require('unicode-2.1.9/bidi-classes/Arabic_Number/symbols');
require('unicode-2.1.9/bidi-classes/Arabic_Number/regex');

require('unicode-2.1.9/bidi-classes/Common_Separator/code-points');
require('unicode-2.1.9/bidi-classes/Common_Separator/symbols');
require('unicode-2.1.9/bidi-classes/Common_Separator/regex');

require('unicode-2.1.9/bidi-classes/European_Number/code-points');
require('unicode-2.1.9/bidi-classes/European_Number/symbols');
require('unicode-2.1.9/bidi-classes/European_Number/regex');

require('unicode-2.1.9/bidi-classes/European_Separator/code-points');
require('unicode-2.1.9/bidi-classes/European_Separator/symbols');
require('unicode-2.1.9/bidi-classes/European_Separator/regex');

require('unicode-2.1.9/bidi-classes/European_Terminator/code-points');
require('unicode-2.1.9/bidi-classes/European_Terminator/symbols');
require('unicode-2.1.9/bidi-classes/European_Terminator/regex');

require('unicode-2.1.9/bidi-classes/Left_To_Right/code-points');
require('unicode-2.1.9/bidi-classes/Left_To_Right/symbols');
require('unicode-2.1.9/bidi-classes/Left_To_Right/regex');

require('unicode-2.1.9/bidi-classes/Other_Neutral/code-points');
require('unicode-2.1.9/bidi-classes/Other_Neutral/symbols');
require('unicode-2.1.9/bidi-classes/Other_Neutral/regex');

require('unicode-2.1.9/bidi-classes/Paragraph_Separator/code-points');
require('unicode-2.1.9/bidi-classes/Paragraph_Separator/symbols');
require('unicode-2.1.9/bidi-classes/Paragraph_Separator/regex');

require('unicode-2.1.9/bidi-classes/Right_To_Left/code-points');
require('unicode-2.1.9/bidi-classes/Right_To_Left/symbols');
require('unicode-2.1.9/bidi-classes/Right_To_Left/regex');

require('unicode-2.1.9/bidi-classes/Segment_Separator/code-points');
require('unicode-2.1.9/bidi-classes/Segment_Separator/symbols');
require('unicode-2.1.9/bidi-classes/Segment_Separator/regex');

require('unicode-2.1.9/bidi-classes/White_Space/code-points');
require('unicode-2.1.9/bidi-classes/White_Space/symbols');
require('unicode-2.1.9/bidi-classes/White_Space/regex');
```

## Author

| [![twitter/mathias](https://gravatar.com/avatar/24e08a9ea84deb17ae121074d0f17125?s=70)](https://twitter.com/mathias "Follow @mathias on Twitter") |
|---|
| [Mathias Bynens](https://mathiasbynens.be/) |

## License

This module is available under the [MIT](https://mths.be/mit) license.
