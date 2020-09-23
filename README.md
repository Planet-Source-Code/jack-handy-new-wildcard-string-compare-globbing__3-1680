<div align="center">

## ^NEW^ \-\- wildcard string compare \(globbing\)


</div>

### Description

matches a string against a wildcard string such as "*.*" or "bl?h.*" etc. This is good for file globbing or to match hostmasks.
 
### More Info
 
1 on match, 0 on no match.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Jack Handy](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/jack-handy.md)
**Level**          |Beginner
**User Rating**    |4.6 (46 globes from 10 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__3-26.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/jack-handy-new-wildcard-string-compare-globbing__3-1680/archive/master.zip)





### Source Code

```
int wildcmp(char *wild, char *string) {
 char *cp, *mp;
 while ((*string) && (*wild != '*')) {
 if ((*wild != *string) && (*wild != '?')) {
  return 0;
 }
 wild++;
 string++;
 }
 while (*string) {
 if (*wild == '*') {
  if (!*++wild) {
  return 1;
  }
  mp = wild;
  cp = string+1;
 } else if ((*wild == *string) || (*wild == '?')) {
  wild++;
  string++;
 } else {
  wild = mp;
  string = cp++;
 }
 }
 while (*wild == '*') {
 wild++;
 }
 return !*wild;
}
```

