# Term Filter
TermFilter is a Java library for checking if two strings have a particular relationship to one another, such as if one string is an anagram of another, or if one string matches another using regular expressions. This library is used in most of the search applications on this web site. The complete list of filters (classes):

* AnagramFilter - Matches terms that are an anagram of the argument passed in the constructor: AnagramFilter(String word, boolean ignoreCase)
* ContainsAllFilter - Matches terms that contain all of strings in the argument passed in the constructor: ContainsAllFilter(String word, boolean ignoreCase), where the space and quotes characters are treated as delimiters
* ContainsFilter - Matches terms that contain the argument passed in the constructor: ContainsFilter(String word, boolean ignoreCase)
* ContainsSomeFilter - Matches terms that contain one or more of the strings in the argument passed in the constructor: ContainsSomeFilter(String word, boolean ignoreCase), where the space and quotes characters are treated as delimiters
* EndsWithFilter - Matches terms that end with the argument passed in the constructor: EndsWithFilter(String word, boolean ignoreCase)
* ExactMatchFilter - Matches terms that are exactly the same as the argument passed in the constructor: ExactMatchFilter(String word, boolean ignoreCase)
* RegexFilter - Matches terms that match the regular expression string passed in the constructor: RegexFilter(String regex, boolean ignoreCase)
* SimilarFilter - Matches terms that are similar to the term passed in the constructor, with a maximum distance also specified in the constructor: SimilarFilter(String word, boolean ignoreCase, int maxDistance) (this class uses the Levenshtein algorithm to compute the distance)
* SoundFilter - Matches terms that sound like the term passed in the constructor: SoundFilter(String word, boolean ignoreCase)
* StartsWithFilter - Matches terms that start with the argument passed in the constructor: StartsWithFilter(String word, boolean ignoreCase)
* WildcardFilter - Matches terms that match the wildcard pattern passed in the constructor: WildcardFilter(String word, boolean ignoreCase) (this class uses the Wildcard code; see that page for more info)

Each of the above filters implements the interface TermFilter, which only has one method: boolean accept(String). The constructor for each filter typically takes the input String and a boolean (whether to ignore the case on matches). The accept() method returns whether the two strings (one passed in the constructor and one passed to accept()) match.

Here's an example, using the StartsWithFilter class:

```
  // Declare a filter for all terms starting with "car", ignoring case
  TermFilter filter = new StartsWithFilter("car", true);
  
  // See if the term matches
  boolean b = filter.accept("Carpet");  // returns true
```

The repository includes an Ant build.xml file. The file includes the following targets of interest:

* dist - Generate the termfilter.jar file
* javadoc - Generate the Javadocs in the docs subdirectory

The source code is released under the MIT license.
