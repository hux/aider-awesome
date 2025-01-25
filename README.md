# aider-awesome
Prompts and helpers that work well with aider-chat 


## WE ARE NOT RESPONSIBILE FOR YOUR API COSTS BY USING THESE COMMMANDS
## FOR AN AVERAGE REACTJS PROJECT, 
# EXPECT TO SPEND 
# $50 to $500 
# to 
# $500 
# FOR EACH OF THESE COMMANDS 
# 
# depending on your configuration.
# eslinting an entire project until all files are 


```
find src/ -type f -name "*.js" -o -name "*.jsx" | while read file; do echo $file; if ! npx eslint --fix "$file" > /dev/null 2>&1; then    msg=$(npx eslint "$file" 2>&1 | tr '\n' ' ');    aider --yes-always --map-tokens 0 --map-refresh always --no-auto-commit --dark-mode --edit-format architect --no-detect-urls --no-suggest-shell-commands --weak-model anthropic/claude-3-5-sonnet-20241022 --message "$msg" --file "$file";  fi; don
```
