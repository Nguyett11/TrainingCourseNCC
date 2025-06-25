# Phần 1: Definition
## 1. Git là gì? 
  - Hệ thống quản lý phiên bản phân tán (Distributed Version Control System).
  - Dùng để quản lý mã nguồn, theo dõi thay đổi và làm việc nhóm.
## 2. Git và GitHub
  - Git là công cụ quản lý mã nguồn.
  - GitHub là dịch vụ lưu trữ Git repository online. (Ngoài ra còn có GitLab, Bitbucket…)
  
# Phần 2: Cài đặt và Cấu hình
## 1. Cài git: Tải tại git-scm.com
## 2. Cấu hình: 
      git config --global user.name "Tên"
      git config --global user.email email@example.com
## 3. Kiểm tra cấu hình: git config –list

# Phần 3: Làm việc với Repository
  - Tạo repo mới: git init
  - Clone repo có sẵn: git clone <url>
  - Kiểm tra trạng thái: git status
  - Thêm thay đổi vào stagging: git add <file> hoặc git add .
  - Commit git commit -m “…”
  - Xem lịch sử commit: git log hoặc git log –oneline
    
# Phần 4: Nhánh (Branch)
  - Tạo nhánh: git branch <Tên nhánh>
  - Chuyển nhánh: git checkout <Tên nhánh>
  - Tạo và chuyển nhanh: git checkout -b <Tên nhánh>
  - Xem danh sách nhánh: git branch
  - Xóa nhánh: git branch -d <Tên nhánh>
    
# Phần 5: Gộp nhánh và xử lý conflict
  - Gộp nhánh: Git merge <nhánh>
  - Xử lý conflict:
    •	Sửa file bị xung đột
    •	Git add <file>
    •	Git commit
  - Rebase: git rebase <nhánh> (nối commit theo dòng thẳng)
    
# Phần 6: Git remote (làm việc với server)
  - Kiểm tra remote: git remote -v
  - Thêm remote: git remote add origin <url>
  - Push lên github: git push -u origin main
  - Pull về máy: git pull origin main
  - Đổi nhánh chính (nếu dùng master): git branch -M main
    
# Phần 7: Các lệnh nâng cao
  - Undo file đã thay đổi: git checkout -- <file>
  - Hủy toàn bộ thay đổi chưa commit: git reset –hard 
  - Hủy 1 commit: git revert <commit-id>
  - Chạy lại commit (soft reset): git reset --soft <commit-id>
  - Xem khác biệt: git diff, git diff –staged
  - Stash (giấu tạm thời thay đổi): git stash, git stash apply
    
# Phần 8: Commit Convention
Quy tắc giúp commit dễ hiểu, rõ ràng, thống nhất khi làm việc nhóm. Ví dụ theo chuẩn Conventional Commits:
               ## <type>(scope): message
  - type: loại commit (feat, fix, refactor, docs, test, chore, ...)
  - scope: phạm vi thay đổi (không bắt buộc)
  - message: mô tả ngắn gọn, rõ ràng
Ví dụ:
  feat(user): add user login form
  fix(api): correct null pointer error
  docs(readme): update project description

# Phần 9: Practices
- Luôn tạo branch mới khi làm tính năng/bugfix (feature/login, bugfix/api-crash)
- Viết commit message rõ ràng, có ý nghĩa
- Pull trước khi push để tránh xung đột
- Không commit file rác hoặc file cấu hình cục bộ (dùng .gitignore)
- Squash commit khi merge vào main để gọn lịch sử



