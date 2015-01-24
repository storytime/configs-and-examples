**Enum to List**

``` java
  private List<String> enumValuesToNamesList(Enum... tEnum) {
          return Lists.transform(Arrays.asList(tEnum), new Function<Enum, String>() {
              @Override
              public String apply(Enum input) {
                  return input.name();
              }
          });
      }

  public List<String> usages() {
      return enumValuesToNamesList(SomeEnum.values());
  }
```
