## Initializing a Repository
### After creating a new folder
নতুন একটি ফোল্ডার তৈরি করার পর নিচের কমান্ডগুলো ব্যবহার করুন:
```bash
git init
```
```bash
git checkout -b main
```
```bash
git remote add origin <repository_url>
```
```bash
git remote -v
```
```bash
git pull origin main # বিশেষ ক্ষেত্রে
```
```bash
git pull origin main --rebase # বিশেষ ক্ষেত্রে
```
```bash
git add .
```
```bash
git commit -m "Initial commit"
```
```bash
git push -u origin main
```

## Branch Management
### Switching branches
একটি ব্রাঞ্চ থেকে অন্য ব্রাঞ্চে যাওয়ার জন্য:
```bash
git checkout <branchname>
```

### Git checkout a remote branch
রিমোট ব্রাঞ্চ চেকআউট করার জন্য:
```bash
git fetch --all
```
```bash
git checkout <remotebranch>
```

### Check which branch you're on
আপনি কোন ব্রাঞ্চে আছেন তা চেক করার জন্য:
```bash
git branch
```
```bash
git branch -r       # রিমোট ব্রাঞ্চ দেখাবে
```
```bash
git branch -a       # সব ব্রাঞ্চ (লোকাল + রিমোট) দেখাবে
```
### Delete Remote and Local Branch
```bash
git branch -D branch-name  # লোকাল ব্রাঞ্চ ডিলিট  
git push origin --delete branch-name  # রিমোট ব্রাঞ্চ ডিলিট  
```

## File and Status Management
### Check file update using Git
ফাইল আপডেট চেক করার জন্য:
```bash
git status
```

## Merging Branches
### Check if the branch is up-to-date
ধরা যাক আপনি মেইন ব্রাঞ্চে আছেন এবং "Tarak" ব্রাঞ্চকে মেইন ব্রাঞ্চের সাথে মার্জ করতে চান:
```bash
git fetch origin
```
```bash
git checkout main
```
```bash
git merge Tarak
```

### If there are conflicts
যদি কনফ্লিক্ট থাকে:
```bash
git status
```
কনফ্লিক্ট ফাইলগুলো খুলুন, সঠিক কোড রেখে কনফ্লিক্ট সমাধান করুন এবং চেঞ্জগুলো স্টেজ করুন:
```bash
git add .
```
```bash
git commit -m "Resolve merge conflicts"
```
```bash
git push origin main
```

## Advanced Git Commands
### Stashing changes
আপনার লোকাল চেঞ্জগুলো কমিট না করেই সংরক্ষণ করতে:
```bash
git stash
```
স্ট্যাশ করা চেঞ্জগুলো পুনরায় প্রয়োগ করতে:
```bash
git stash apply
```
স্ট্যাশ লিস্ট দেখতে:
```bash
git stash list
```
নির্দিষ্ট একটি স্ট্যাশ ড্রপ করতে:
```bash
git stash drop stash@{index}
```

### Rewriting history
কমিটগুলো পরিষ্কার করতে ইন্টারেক্টিভ রিবেস:
```bash
git rebase -i HEAD~<number_of_commits>
```

### Undoing changes
ফাইলকে সর্বশেষ কমিটেড অবস্থায় রিসেট করতে:
```bash
git checkout -- <file>
```
শেষ কমিটটি আনডু করুন কিন্তু চেঞ্জগুলো স্টেজড রাখুন:
```bash
git reset --soft HEAD~1
```
শেষ কমিটটি আনডু করুন এবং চেঞ্জগুলো বাতিল করুন:
```bash
git reset --hard HEAD~1
```

### Cleaning up untracked files
আনট্র্যাকড ফাইল এবং ডিরেক্টরি রিমুভ করতে:
```bash
git clean -fd
```

### Tagging
নতুন একটি ট্যাগ তৈরি করতে:
```bash
git tag -a <tag_name> -m "Tag message"
```
ট্যাগগুলো রিমোটে পুশ করতে:
```bash
git push origin --tags
```

### Viewing logs
ডিটেইলড কমিট হিস্টোরি দেখতে:
```bash
git log --oneline --graph --decorate --all
```

### Bisecting
বাগ ইনট্রোডিউস করা কমিট খুঁজে বের করতে:
```bash
git bisect start
git bisect bad
git bisect good <commit_hash>
```

### Industry-Level Commands
### Squashing commits
একাধিক কমিটকে একটি কমিটে পরিণত করতে:
```bash
git rebase -i HEAD~<number_of_commits>
```

### Cherry-picking
নির্দিষ্ট একটি কমিট অন্য ব্রাঞ্চে প্রয়োগ করতে:
```bash
git cherry-pick <commit_hash>
```

### Viewing contributors
প্রজেক্টে কারা অবদান রেখেছেন তা দেখতে:
```bash
git shortlog -sn
```

### Shallow clone
রিপোজিটরির একটি নির্দিষ্ট ডেপথ ক্লোন করতে:
```bash
git clone --depth=<depth> <repository_url>
```