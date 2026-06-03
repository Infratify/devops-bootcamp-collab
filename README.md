# Bootcamp DevOps 2026 — Repo Kolaborasi

Repo latihan untuk sesi **GitHub 2**: belajar aliran *fork → pull request → code
review* dengan menyumbang ke repo orang lain (repo ini!).

Setiap peserta menambah **satu fail** `<username-github>.md`. Nama fail = username
GitHub anda (unik) — jadi tiada dua peserta berlanggar semasa merge.

## Cara sumbang

```bash
# 1. Fork + clone repo ini ke laptop
gh repo fork Infratify/devops-bootcamp-collab --clone
cd devops-bootcamp-collab

# 2. Ambil username GitHub anda + cipta branch
GH_USER=$(gh api user --jq .login)
git checkout -b tambah-$GH_USER

# 3. Tambah fail anda (lihat CONTOH.md untuk format)
echo "# Peserta: $GH_USER" > "$GH_USER.md"

# 4. Commit + push ke fork anda
git add "$GH_USER.md"
git commit -m "Tambah $GH_USER.md"
git push -u origin tambah-$GH_USER

# 5. Buka pull request ke repo asal
gh pr create --repo Infratify/devops-bootcamp-collab --base main \
  --title "Tambah $GH_USER" --body "Sumbangan dari $GH_USER"
```

## Code review

Sesiapa boleh **semak** PR di repo awam ini — tidak perlu *write access*:

```bash
gh pr view <N>   --repo Infratify/devops-bootcamp-collab     # baca PR
gh pr diff <N>   --repo Infratify/devops-bootcamp-collab     # lihat perubahan
gh pr review <N> --repo Infratify/devops-bootcamp-collab --comment         --body "..."
gh pr review <N> --repo Infratify/devops-bootcamp-collab --approve         --body "LGTM"
gh pr review <N> --repo Infratify/devops-bootcamp-collab --request-changes --body "..."
```

Hanya **merge** memerlukan *write access* (instruktur).

> Lab terakhir GitHub 2: peserta kembali untuk PR kedua menambah URL laman
> GitHub Pages mereka (`https://<username>.github.io`) ke fail kad masing-masing.
