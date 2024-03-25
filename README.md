
Stream műveletek:
- countries.stream() Stream létehozás a countires objektumra
- map(Country::name) name szerint fogja csinálni
- forEach(System.out::println) végig iterál az objektum összes elemén és kiírja őket

Sorted műveletek:
- sorted(Comparator.nullsFirst(Comparator.naturalOrder())) a nullok lesznek először utána abc szerint a többi eredmény
- sorted(Comparator.nullsLast(Comparator.reverseOrder())) a nullok a végén és csökkenő sorrend
- sorted() növekvő sorrendbe rendezi
- sorted(Comparator.nullsFirst(Comparator.comparingInt(String::length).thenComparing(Comparator.naturalOrder()))) dupla sort

Numeric műveletek:
- mapToLong(Country::population) Long típusura alakítja a map értékét
- mapToInt(Country::population) Inttípusura alakítja a map értékét
- mapToDouble(Country::population) Double típusura alakítja a map értékét
- max() maximumot adja vissza
- min() minimumot adja vissza
- getAsLong() A long típusú értéket ember számára olvahatóvá teszi
- getAsDouble() A double típusú értéket ember számára olvahatóvá teszi
- average() átlagot ad vissza
- summaryStatistics() Long, double vagy int Stream esetében használható

Filter műveletek:
- filter(country -> country.region() == Region.EUROPE) Megszűri a feltétel alapján
- filter(country -> country.independent()) ahol True a boolean
- filter(Country::independent) ahol True a boolean
- filter(country -> country.population() < 100)
- filter(country -> country.name().startsWith("H"))
- filter(country -> !country.translations().containsKey("fa")) nem tartalmazza a "fa" stringet
- filter(country -> country.region() == Region.EUROPE || country.region() == Region.ASIA)
- filter(Objects::nonNull)
- filter(country -> country.translations().size() > 0)
- filter(s -> s.toLowerCase().contains("island"))
- filter(s -> { String t = s.toLowerCase(); return t.charAt(0) == t.charAt(t.length() - 1); })

FlatMap műveletek:
- flatMap(country -> country.timezones().stream())
- flatMap(country -> country.translations().keySet()) a keyset csak egy listát ad vissza

Egyéb műveletek:
- boxed() long streamen csak egy egy long objektumot ad vissza, pl. sorted()-et alapból nem lehet longra, de boxolva lehet
- limit(5) csak az első 5 elemet adja vissza
- anyMatch(country -> country.population() == 0) true vagy false
- allMatch(country -> country.timezones().size() > 0) true vagy false
- findFirst() legelső elemet adja vissza
- distinct() azonos elemek esetén csak egyszer jeleníti meg őket
- reduce(BigDecimal::add) összeadja a BigDecimalokat a streamben
- BigDecimal::subtract: Kivonás művelet.
- BigDecimal::multiply: Szorzás művelet.
- BigDecimal::divide: Osztás művelet.
- Bármely egyedi művelet megadása egy saját BinaryOperator lambda kifejezésben.
- collect(Collectors.joining(",")) vessző alapján egymásmellé írja a stringeket
- entrySet() az összes kulcs-érték párt visszaadja
- collect(Collectors.groupingBy(word -> word.charAt(0))) visszaadja a csoportokat az első betű alapján

