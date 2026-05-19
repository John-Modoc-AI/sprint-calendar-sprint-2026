# Sprint Calendar

Static, password-protected sprint calendar. Page content is AES-encrypted client-side using [staticrypt](https://github.com/robinmoisson/staticrypt), so it's not visible in view-source until the password is entered.

## Files

- `index.src.html` — editable plaintext source. **Edit this.**
- `index.html` — encrypted build output that gets served to users. **Do not edit by hand.**
- `.staticrypt.json` — local salt cache, gitignored.

## Password

- Password: `fevercoach`
- Hint shown on the gate: `Hint: our app name (all lowercase)`

## Editing workflow

1. Edit `index.src.html`.
2. Regenerate the encrypted `index.html`:

   ```
   npx staticrypt index.src.html -p fevercoach --short \
     --template-title "Sprint Calendar" \
     --template-instructions "Hint: our app name (all lowercase)" \
     --template-button "Enter" \
     --template-error "Wrong password" \
     -d build && mv build/index.src.html index.html && rmdir build
   ```

3. Commit both `index.src.html` and `index.html`.

If staticrypt isn't installed globally yet:

```
npm install -g staticrypt
```
