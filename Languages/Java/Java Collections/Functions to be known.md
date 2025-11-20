#### Functions for Sorting data in Lists(ArrayList, Vector, Stack, LinkedList):
- Collections.sort(List_Name);
- List.sort(Use Null(follows natural order) or Mostly use Comparator);

##### Comparator:
- Used for Sorting Objects.
- need to import Package.

Common Comparator Methods (Java 8+)
- `Comparator.naturalOrder()` - Common Use For: Strings, numbers, dates.
- `Comparator.reverseOrder()` - Common For: Descending sorting.
- `Comparator.comparing(Function)` - Common For: Custom classes (e.g., sort by name, age, etc.).
- `Comparator.comparingInt(ToIntFunction)`  - Common For: Sorting by an `int` field in a custom object.
- `thenComparing(...)` — for secondary sorting - Common For: Multi-field sort (e.g., sort by name, then by age).

|Collection Type|Sort Method|Notes|
|---|---|---|
|`List` types|`Collections.sort(list)`|Classic way|
||`list.sort(comparator)`|Modern, Java 8+|
|Arrays|`Arrays.sort(array)`|For primitive or object arrays|
|`Set`, `Map`|Use `TreeSet`, `TreeMap`, or convert to `List` and sort manually||
