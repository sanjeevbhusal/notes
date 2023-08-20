
Add this code to jest configuration in package.json

```
"moduleNameMapper": {
  "^src/(.*)$": "<rootDir>/$1"
}
```

More Information: https://stackoverflow.com/questions/56703570/unable-to-run-tests-because-nest-cannot-find-a-module