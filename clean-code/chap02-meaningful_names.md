# Meaningful Names

### Use intention-revealing names
- e.g. While iterating in an array
  - What objects do the array hold?
  - Meaning of the array index
  - Any (constant) value that is being compared with the array element

### Avoiding disinformation
- Information : spelling similar concepts similarly
- Disinformation : Inconsistent spellings
  
### Meaningful distinctions
- not-to-do
  - Number series variables (e.g. `n1`, `n2`, ...)
  - Noise words (plural form, meaningless addition (e.g. `info`, `amount`, ..))
- **READERS** should feel distinguished

### Searchable names
- Length of a name should be proportional to its scope
  - e.g. Signle letter only as a local variable
  - e.g. Capitalized/long ,letters (e.g. `MAX_CLASSES_PER_STUDENT`) for large scopes
    - *(think of environment variables)*
  - It is very good to utilize `grep` and `git grep` to easily search for names.
  
### Avoid mental mapping
- e.g. `i,j,k` in iteration

### Naming strategy per code elements
- Class
  - Combine **nouns**
  - e.g. `Customer`, `WikiPage`, ..
- Methods
  - Start with `verb`
  - e.g. `getSomething`, `deletePage`, getter and setter
    - *(in scala, getter/setter not used. why?)*
- Etc.
  - Adding `_` in the prefix of the variable?
  - Consider different style for each language
  - Q. What would be the good convention for system programming?
### Rename!
