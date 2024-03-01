# pipex

## error handling

⚠️ if you are not sure, compare behavior to bash!

### broken inputs

when the first command fails, the second command should still be executed & the outfile created (**_even if it means creating an empty file)_**!

```./pipex nonexisting cat ls out``` 

-> ls output in out

-> error message in terminal

```./pipex nonexisting cat cat out```

-> empty outfile created/existing outfile overwritten

-> error message in terminal


