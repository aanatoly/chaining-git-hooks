# chaining git-hooks
Here you can find collection of usefull git hooks and a script
to chain them. 

With it, you can have many pre-commit scripts without explcitly writing 
a wrapper to call them one by one.

## Hooks

 * pre-commit-01-rm-trailing-ws - fails commit if file has trailing whitespace
 * pre-commit-02-pep8 - fails commit if python file is not pep8 compliant,
   ignores other files.
 * prepare-commit-msg-01-ref-issues - inserts issue reference into commit
   message, then lets user edit it.

## Usage 
Copy `hook-chain` script to the `.git/hooks` directory
```
cd my-project/.git/hooks
git clone https://github.com/aanatoly/chaining-git-hooks.git /tmp/cgh
cp /tmp/cgh/hook-chain .
```
Copy relevant hooks and name them TYPE-NO-NAME. For example, to have 2
   pre-commit hooks, do this:
```
cp /tmp/cgh/pre-commit-[0-9]*  .
```
Create link, named as original hook pointing to `hook-chain`
```
rm -f pre-commit
ln -sf hook-chain pre-commit
```
That is it.
