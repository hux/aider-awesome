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
# No support will be provided for any of these commands. They are merely examples of what aider can do.
# these are referred to as DESTRUCTIVE commands. BEWARE and TAKE CARE you have been WARNED
#
---
---
---


### eslinting an entire project until all files are 
```
cd my-code-base && \
time find src/ -type f -name "*.js" -o -name "*.jsx" | while read file; do echo $file; if ! npx eslint --fix "$file" > /dev/null 2>&1; then    msg=$(npx eslint "$file" 2>&1 | tr '\n' ' ');    aider --yes-always --map-tokens 0 --map-refresh always --no-auto-commit --dark-mode --edit-format architect --no-detect-urls --no-suggest-shell-commands --weak-model anthropic/claude-3-5-sonnet-20241022 --message "$msg" --file "$file";  fi; don
```

### in-line code documentation
```
cd my-code-base && \
time for filename in $(find . -type f \( -name "*.js" -o -name "*.py" -o -name "*.tsx" \) -not -path "*/node_modules/*" -not -path "*/deployed_static/*" -not -path "*/migrations/*" -not -path "*/tests/*" -not -path "*/__init__.py" );do echo "---" && echo $filename && aider --no-auto-commit --edit-format diff-fenced --yes --dark-mode --message "Please review this file and add comments to the code and a summary at the top of file explaining briefly what it does. Do not change any existing comments, simply comment on the uncommented lines that are relevant enough to the explaination of the function" --file $filename ; done
```

### Fixing PyFlakes errors 
```
cd my-code-base && \
time while IFS= read -r line; do filename=$(echo "$line" | cut -d':' -f1); echo "Processing: $line"; aider --no-auto-commit --yes-always --map-tokens 768 --map-refresh always --dark-mode --edit-format diff --file $filename --message "$line"; done < <(flake8 --max-line-length 120 .)
```
