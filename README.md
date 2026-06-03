# Bootcamp DevOps 2026 — Repo Kolaborasi

Repo latihan untuk sesi **GitHub 2**: belajar aliran *fork → pull request → code
review* dengan menyumbang ke repo orang lain (repo ini!).

Setiap peserta menambah **satu fail** `<username>.md`. Tiada dua peserta
menyentuh fail yang sama — jadi tiada konflik semasa merge.

## Cara sumbang

```bash
# 1. Fork + clone repo ini ke laptop
gh repo fork Infratify/bootcamp-collab --clone
cd bootcamp-collab

# 2. Cipta branch baharu
git checkout -b tambah-$USER

# 3. Tambah fail anda (lihat CONTOH.md untuk format)
echo "# Peserta: $USER" > "$USER.md"

# 4. Commit + push ke fork anda
git add "$USER.md"
git commit -m "Tambah $USER.md"
git push -u origin tambah-$USER

# 5. Buka pull request ke repo asal
gh pr create --repo Infratify/bootcamp-collab --base main \
  --title "Tambah $USER" --body "Sumbangan dari $USER"
```

## Code review

Sesiapa boleh **semak** PR di repo awam ini — tidak perlu *write access*:

```bash
gh pr view <N>   --repo Infratify/bootcamp-collab     # baca PR
gh pr diff <N>   --repo Infratify/bootcamp-collab     # lihat perubahan
gh pr review <N> --repo Infratify/bootcamp-collab --comment         --body "..."
gh pr review <N> --repo Infratify/bootcamp-collab --approve         --body "LGTM"
gh pr review <N> --repo Infratify/bootcamp-collab --request-changes --body "..."
```

Hanya **merge** memerlukan *write access* (instruktur).
