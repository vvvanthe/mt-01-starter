# Buổi 02 — Khởi tạo dự án: từ template thành dự án của bạn

> Nguồn của buổi này: [đề bài MT-01](../de-bai.md)
> · [khung đánh giá](00-khung-danh-gia.md) · [repo mẫu](repo-mau/README.md)
> Thời lượng 120' · Trong repo dự án, giáo trình nằm ở `docs/giao-trinh/`, đề bài ở `docs/de-bai.md`

## Mentor xong buổi này phải làm được

- Dựng được dự án chạy từ template: môi trường ảo, `.env`, `make run`, Swagger UI mở được.
- **Đối chiếu tài liệu với code** và chỉ ra chỗ lệch — trên chính template của chương trình, không phải ví dụ dựng.
- Bắt agent **dẫn nguồn trong `docs/giao-trinh/`** rồi tự mở file đó kiểm lại — và phân biệt được câu nó đọc được với câu nó phải chạy lệnh mới biết.

## Câu đội sẽ hỏi mà buổi này trả lời

1. *"Em làm theo README mà nó lỗi, sao vậy anh?"*
2. *"Nhóm em chốt đề rồi, dựng Docker với CI luôn cho chắc nhé?"*
3. *"Em để key trong file config cho tiện, có sao không?"*

## Điều kiện trước

Python 3.12 (hoặc 3.11), Git, `gh` đã đăng nhập. Agent coding đã cài. Đã nhận link
`mt-01-starter` từ người dạy. Chưa cần API key của LLM.

---

## Slide (30 phút)

| # | Tiêu đề slide | Nội dung trên slide | Người trình bày nói gì |
|---|---|---|---|
| 1 | Hôm nay không viết logic, hôm nay dựng nền | Bốn thứ phải có cuối buổi: môi trường chạy được · `.env` không bị commit · Swagger mở được · PR đầu đã merge. | Mentor mới hay coi buổi setup là buổi phụ. Thực tế đây là buổi quyết định tuần 4 của đội có deploy được không. Câu "trên máy em chạy được" bắt đầu từ chỗ setup làm tắt. |
| 2 | Không tự tạo repo | Repo của đội do hệ thống **sinh sẵn** từ template, nằm trong org của khoá. Repo đội tự tạo ngoài org **không bắn webhook về hệ thống chấm** và không được tính là bài nộp. | Đây là lỗi mất điểm oan và rất hay gặp. Mentor phải biết để chặn ngay tuần 1. Chưa thấy repo thì báo BTC, đừng tự tạo. |
| 3 | Template chính thức, đã lược: 94 → 68 file | **Giữ:** `src/agents/` (buổi 04) · `src/api/` `src/models/` (buổi 08) · `tests/` (buổi 10) · Docker, CI, `ruff.toml` (buổi 12) · `scripts/` + 6 cấu hình hook (buổi 02) · `ARCHITECTURE.md` `JOURNAL.md` `WORKLOG.md` (deliverable 3, 8, 9). **Xoá:** `docs/guide/` 37 file và `docs/COHORT3_REPORT.md`. | Nói rõ: không viết lại khung, đây **là** template thật, chỉ xoá hai mục cả 15 buổi không dùng. Vì sao xoá `docs/guide/`: đó là một bộ tài liệu **song song** mà khoá này không dạy theo — khoá dùng giáo trình riêng ở `docs/giao-trinh/`. Giữ hai bộ tài liệu lệch nhau trong một repo là cách nhanh nhất để agent trả lời sai rất tự tin về thứ không có trong khoá. Bảng lược-giữ đầy đủ: `DA-LUOC.md` trong repo. |
| 4 | Chọn tầng khởi đầu | **Tầng 1 — prototype**: tuần 1–2, chưa chắc user cần gì, cần thứ cho 5 người xem trong 48 giờ. Không server, không Docker. **Tầng 2 — repo của đội**: đã có USP và ≥5 feedback, build nghiêm túc. | Trả lời câu hỏi số 2 của đội. Đội dựng full Docker/CI tuần 1 khi đề chưa validate thì mất 3 tuần đầu "set up hạ tầng". Ngược lại đội đã chắc đề mà vẫn code prototype tay thì demo ngày bị lỗi dưới tải. Chuyển tầng thì mang theo đúng hai thứ: câu hỏi user thật và USP đã validate. |
| 5 | Môi trường, và cách đọc thông báo lỗi | `python3 -m venv .venv` → `source .venv/bin/activate` → `pip install -r requirements.txt`. **Đọc lỗi:** tìm dòng `ERROR`, hoặc dòng cuối của khối `Traceback` — **bỏ qua `[notice]` và `WARNING`**. | Giải thích venv bằng một câu: nó là hộp thư viện riêng cho dự án này, để dự án khác không phá nó và nó không phá máy bạn. Dấu hiệu quên bật venv: `No module named ...`. Về cách đọc lỗi, nói thẳng một chỗ dễ sai: "đọc dòng cuối" chỉ đúng với Traceback của Python — pip in `[notice]` **sau** dòng `ERROR`, nên dòng cuối lại là lời khuyên nâng cấp pip. Lab bước 2 sẽ gặp đúng trường hợp đó. |
| 6 | Ba chỗ template thật đang lệch | **(1)** README bảo `pip install -e ".[dev]"` nhưng repo không có `pyproject.toml` → lệnh lỗi; đúng là `pip install -r requirements.txt`. **(2)** `make test` ra **2 passed, 3 errors** ngay khi vừa clone. **(3)** `ci.yml` khai `pull_request: branches: [main]` → PR nhắm `develop` **không** kích hoạt CI. | Slide quan trọng nhất của buổi. Cả ba là lỗi **thật** trong template chính thức, kiểm được trong 10 giây mỗi cái. Đừng tiết lộ trước — lab cho họ tự gặp. Nói rõ: không phải người viết template kém; tài liệu và code đi lệch nhau theo thời gian ở mọi dự án, và việc của mentor là **người đối chiếu**. Chỗ (2) học viên tự sửa ở lab bước 7. |
| 7 | Biến môi trường: không bao giờ hardcode | `.env.example` commit lên · `.env` **không bao giờ** · `.env` đã nằm trong `.gitignore`. Key lỡ đẩy lên GitHub thì phải **thu hồi key**, không phải xoá commit. | Trả lời câu hỏi số 3. Nhấn câu cuối: xoá commit không cứu được gì, vì key đã nằm trong lịch sử và trên server của GitHub. Đây là chuyện đã xảy ra ở Cohort-4: một đội để credential của runner trong một nhánh, và cách xử lý là thu hồi runner trước, xoá nhánh sau. |
| 8 | `git status` sạch ≠ đã commit hết | `.gitignore` của template bỏ qua **cả `data/`** — hợp lý cho dữ liệu runtime, nhưng dữ liệu đề bài cũng nằm đó, nên `rubric.yaml` và đề cương mẫu **không bao giờ được commit** mà `git status` vẫn sạch. Phép kiểm: `git ls-files \| grep data`. | Người dạy đã sửa khi dựng repo (`data/` → `data/*` + mở lại ba mục), nhưng bài học thì ở lại. Thứ bị `.gitignore` chặn **không xuất hiện ở đâu cả** — không trong `git status`, không trong `git add .`. Đội sẽ mất file theo đúng cách này: hỏi "sao máy em có mà máy bạn không có". Phép kiểm đúng là `git ls-files`, không phải `git status`. |
| 9 | Git workflow: không ai commit thẳng vào main | `main` được bảo vệ → nhánh `develop` → nhánh tính năng → PR → review → merge. | Một đội Cohort-4 có `main` đứng yên ba tuần trong khi 21 nhánh khác chạy. Mentor chỉ nhìn `main` sẽ kết luận sai rằng đội không làm gì. Bài học: hỏi đội **merge vào đâu** trước khi đánh giá tiến độ. |
| 10 | Chạy server lần đầu | `make run` → `http://localhost:8000/docs` Swagger UI · `GET /health` trả `{"status":"ok"}`. | Làm thật trên máy chiếu. Swagger UI là món quà cho mentor không-biết-code: nó là giao diện bấm được để thử API, không cần viết dòng nào. Buổi 08 sẽ dùng lại nó để duyệt API của đội. |
| 11 | Đề MT-01 — ba tầng, không chỉ đề cương | **A. Trợ lý người học** hỏi đáp grounded + hỗ trợ ESL · **B. Chuẩn hóa môn học** rubric 6 tiêu chí, giảng viên duyệt · **C. Bức tranh chương trình** số tổng hợp ẩn danh. | Nhắc lại đề cho rõ, vì buổi 01 có người hiểu hẹp thành "chỉ soạn đề cương". Hệ thống gánh cả ba tầng: người học, môn học, chương trình. Chuẩn hóa đề cương chỉ là năng lực B. |
| 12 | Học cùng AI — quy tắc trong repo | `CLAUDE.md`: agent phải **dẫn nguồn, nêu rõ file nào dòng nào** · kết thúc mỗi việc bằng **một phép kiểm** để bạn tự chạy · **không quyết định thay bạn** · **không làm hộ** phần đang là bài học. | Đọc bốn quy tắc này to. Chúng nằm trong repo nên agent tự đọc, không cần nhắc mỗi lần. Nhấn quy tắc 2: phép kiểm là phần được chấm, không phải code agent sinh ra. Và đừng để agent tự chạy phép kiểm rồi báo đạt. |

---

## Thực hành (60 phút) — Dựng nền, và tìm chỗ tài liệu nói khác code

**Sau lab, bạn có:** repo riêng chạy được, `.env` an toàn, Swagger mở được, AI logging đã cài,
`make test` xanh, một PR đã merge, và ba dòng `JOURNAL.md` ghi chỗ tài liệu lệch code bạn tự tìm ra.

### Bước 1 — Repo riêng từ template (6')

```
1. Mở link mt-01-starter người dạy gửi
2. "Use this template" → "Create a new repository"
3. Tên: mt-01-<tên-bạn> · Private · Create
```

Đừng bấm **Fork**. Template cho bạn repo độc lập với lịch sử commit sạch từ commit đầu của bạn.

```bash
gh repo clone <TÊN-BẠN>/mt-01-<tên-bạn>
cd mt-01-<tên-bạn>
ls docs/giao-trinh/ docs/de-bai.md   # giáo trình và đề bài nằm trong repo
```

**Phép kiểm:** `git remote -v` trỏ về repo của bạn. Mở `DA-LUOC.md` đọc 2 phút — nó nói repo này
đã lược gì khỏi template và vì sao.

### Bước 2 — Làm theo README, và gặp lỗi thật (10') ⭐

Mở `README.md`, tìm bước cài dependencies, **làm đúng như nó viết**:

```bash
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -e ".[dev]"          # đúng như README bảo
```

Lệnh này **sẽ lỗi** (exit code 1). Đừng sửa ngay — làm ba việc theo thứ tự:

```bash
# 1. Tìm dòng bắt đầu bằng ERROR, bỏ qua các dòng [notice]
# 2. File mà lệnh đó cần có tồn tại không?
ls pyproject.toml
# 3. Repo thật sự khai dependencies ở đâu?
head -5 requirements.txt
```

Dòng lỗi thật là: `ERROR: ... does not appear to be a Python project: neither 'setup.py' nor
'pyproject.toml' found.`

> **Một chỗ tinh vi, và nó sửa chính quy tắc ở slide 5.** Dòng `ERROR` này **không** phải dòng
> cuối cùng — pip in thêm hai dòng `[notice] A new release of pip is available` *sau* nó. Đọc đúng
> dòng cuối thì bạn gặp lời khuyên nâng cấp pip, không gặp lỗi.
>
> Quy tắc đúng: **tìm dòng `ERROR`, hoặc dòng cuối của khối `Traceback`** — bỏ qua `[notice]` và
> `WARNING`. Quy tắc "đọc dòng cuối" chỉ đúng với Traceback của Python.
>
> Đây là lý do mentor phải tự chạy thử trước khi dạy. Tôi phát hiện chỗ này khi chạy thật, không
> phải khi viết bài.

Rồi cài cho đúng: `pip install -r requirements.txt`

**Đạt khi** `JOURNAL.md` có ba dòng: lệnh trong README là gì, vì sao nó lỗi, lệnh đúng là gì.

Đây là lỗi **thật** trong template chính thức — không ai dựng ra để bạn tập. Tài liệu và code đi
lệch nhau theo thời gian ở mọi dự án. Đội của bạn sẽ gửi đúng câu *"em làm theo README mà nó lỗi"*,
và việc của mentor là **đối chiếu**, không phải đoán.

### Bước 3 — `.env`, và `git status` sạch không có nghĩa là đã commit (8')

```bash
cp .env.example .env
git check-ignore -v .env     # phải in ra dòng .gitignore đang chặn nó
git status --short            # KHÔNG được thấy .env
```

**Đạt khi** cả hai lệnh ra như trên. Thấy `.env` trong `git status` thì dừng, gọi người dạy —
commit nhầm một lần là phải **thu hồi key**, không phải xoá commit.

Rồi làm phép kiểm ngược lại, cái này quan trọng hơn:

```bash
git ls-files | grep data        # phải thấy 4 file trong data/
```

`.gitignore` của template bỏ qua **cả `data/`** — hợp lý cho dữ liệu runtime, nhưng dữ liệu đề bài
cũng nằm đó. Nếu không sửa, `rubric.yaml` và đề cương mẫu **không bao giờ được commit**, mà
`git status` vẫn báo sạch. Người dạy đã sửa khi dựng repo (xem `DA-LUOC.md`), nhưng bài học thì ở
lại: **`git status` sạch không có nghĩa là mọi thứ đã được commit.** Thứ bị `.gitignore` chặn thì
không xuất hiện ở đâu cả.

### Bước 4 — Chạy server, mở Swagger (8')

```bash
make run
```

Mở `http://localhost:8000/docs`. **Phép kiểm** (tab terminal thứ hai, giữ server chạy):

```bash
curl -s localhost:8000/health
```

**Đạt khi** trả `{"status":"ok", ...}` và Swagger UI hiện danh sách endpoint.

Bấm thử một endpoint: **Try it out** → **Execute**. Đây là công cụ mentor dùng lại suốt 6 tuần để
duyệt API của đội **mà không cần viết code**. Buổi 08 dùng nó để gọi API bằng vai sai và xem server
có trả 403 không.

### Bước 5 — AI logging hooks (6')

```bash
bash scripts/setup_hooks.sh
```

**Phép kiểm:**
```bash
ls -a .git/hooks/ | grep pre-push
```

**Đạt khi** hook `pre-push` tồn tại. Deliverable số 4 xong trong một lệnh.

Quy tắc: **đừng gọi tay** `scripts/log_*` — hook tự chạy khi `git push`, gọi tay tạo log giả
(xem `.agents/rules/ai-log-hook.md`). Hook báo lỗi thì **đừng** bypass bằng `--no-verify`: push
được nhưng log không được submit, và một tuần sau mới phát hiện thì đã mất dữ liệu cả tuần.

### Bước 6 — Bắt agent dẫn nguồn (8') ⭐

Giờ mới mở agent. Repo đã có `CLAUDE.md` buộc nó dẫn nguồn — thử xem nó làm thật không:

```
Bằng chứng tối thiểu của gate G4 là gì? Trả lời ngắn, nêu rõ file nào mục nào trong repo này
bạn đọc được điều đó.
```

**Tự mở file đó kiểm lại** — đáp án nằm ở `docs/giao-trinh/00-khung-danh-gia.md` §1. Rồi hỏi câu
thứ hai, câu này có bẫy:

```
Repo này có bao nhiêu file đang được git theo dõi?
```

**Phép kiểm:**
```bash
git ls-files | wc -l
```

Câu một agent **đọc được** trong repo. Câu hai thì **không có file nào ghi sẵn câu trả lời** — muốn
đúng thì phải chạy lệnh. Nhiều agent vẫn trả lời bằng một con số nghe rất hợp lý. Đó là hai lỗi
khác nhau và cách xử lý khác nhau hoàn toàn:

| Agent làm gì | Mentor xử lý thế nào |
|---|---|
| Dẫn nguồn một file có thật, trích đúng | Mở file đó đọc lại. Đây là cách làm việc đúng. |
| Dẫn nguồn một file có thật nhưng trích sai mục | Chỉ vào đúng mục. Lỗi đọc, sửa bằng nguồn. |
| Trả lời con số mà không chạy lệnh nào | **Đòi lệnh.** Không có lệnh thì không có câu trả lời. |

> `CLAUDE.md` trong repo đã viết sẵn quy tắc này: câu hỏi về trạng thái thật của repo thì agent
> phải đưa ra lệnh cho bạn tự chạy, không được đoán. Buổi hôm nay là lần bạn kiểm xem nó có tuân
> không.

**Đạt khi** `JOURNAL.md` có dòng: agent trả lời gì, số thật bao nhiêu, kiểm bằng lệnh nào.

### Bước 7 — Làm test xanh: bài "học cùng AI" đầu tiên (10') ⭐

```bash
make test
```

**2 passed, 3 errors.** Template chính thức có test đỏ ngay khi vừa clone. Lần này bạn **sửa** nó,
với agent, theo đúng quy tắc trong `.agents/rules/hoc-cung-ai.md`:

```
make test cho 2 passed, 3 errors. Dòng lỗi nói: "requested an async fixture 'client', with no
plugin or hook that handled it."
Đọc requirements.txt và tìm trong repo xem có file cấu hình pytest nào chưa.
Giải thích nguyên nhân trong 2 câu, rồi đề xuất bản sửa NHỎ NHẤT.
Chưa sửa gì cả — nói cho tôi biết sẽ sửa file nào, rồi dừng chờ tôi đồng ý.
```

Agent phải chỉ ra: `pytest-asyncio` đã có trong `requirements.txt`, nhưng repo **không có**
`pytest.ini`, `setup.cfg` hay `pyproject.toml` để đặt `asyncio_mode`. Đồng ý thì nó tạo:

```ini
[pytest]
asyncio_mode = auto
testpaths = tests
```

**Phép kiểm:**
```bash
make test                  # phải ra 5 passed
ruff check src/ tests/     # phải ra All checks passed — CI cũng chạy lệnh này
```

**Đạt khi** `5 passed`. Ba dòng cấu hình đổi test từ đỏ sang xanh, và điểm cần rút ra là: **CI xanh
là thứ bạn làm ra, không phải thứ bạn được phát.** Đội nào nhận template rồi để test đỏ suốt 6 tuần
thì tuần 6 không ai dám sửa gì nữa, vì không còn cách phân biệt lỗi mới với lỗi cũ.

### Bước 8 — PR đầu tiên, và một cái bẫy trong CI (4')

```bash
git checkout -b develop && git push -u origin develop
git checkout -b chore/setup-buoi-02
git add JOURNAL.md pytest.ini
git commit -m "chore: cau hinh pytest asyncio; journal buoi 02"
git push -u origin chore/setup-buoi-02
gh pr create --fill --base develop
```

Mở tab **Actions**. **PR này không kích hoạt CI.** Vì sao? Mở `.github/workflows/ci.yml` phần `on:`:

```bash
grep -A5 "^on:" .github/workflows/ci.yml
```

Nó khai `pull_request: branches: [main]` — PR nhắm vào `develop` không chạy workflow nào. Merge rồi
mới thấy CI chạy, vì `push: branches: [main, develop]` có bắt `develop`:

```bash
gh pr merge --squash --delete-branch
gh run list --limit 3
```

**Đạt khi** `gh run list` có một lần chạy **thành công** sau khi merge.

Ghi một dòng `JOURNAL.md` về bẫy này. Đội sẽ mở PR, thấy không có CI, rồi kết luận "CI hỏng rồi
anh" — trong khi CI chỉ không được cấu hình chạy cho nhánh đích đó. **Không có tích xanh không
đồng nghĩa với test đỏ.**

## Bài tập chéo (20 phút) — Đổi vai: "em làm theo README mà nó lỗi"

Ghép cặp. A làm **thành viên đội**, B làm **mentor**. 10 phút rồi đổi vai.

**A nhắn ba tin, mỗi tin cách nhau một phút, đọc nguyên văn:**
1. *"Anh ơi em cài không được, nó đỏ hết màn hình."*
2. *(gửi ảnh chụp một màn hình đầy chữ)* *"Đây anh."*
3. *"Nhóm em chốt đề rồi, em dựng Docker với CI luôn cho chắc nhé?"*

**B phải làm được ba việc:**
- Tin 1: hỏi **đúng một câu** để lấy thông tin có ích — *"dòng cuối cùng của thông báo lỗi viết gì?"* Không hỏi "em thử lại chưa".
- Tin 2: **không chấp nhận ảnh chụp.** Yêu cầu dán **nguyên văn dòng cuối**. Rồi hướng A tới việc tự đọc dòng đó, không nói kết luận hộ.
- Tin 3: hỏi đội đang ở **tầng khởi đầu** nào, và *"đã có USP và 5 feedback người thật chưa?"* trước khi đồng ý cho dựng hạ tầng.

**Chấm:** mỗi việc 1 điểm. B dưới 2/3 thì làm lại với cặp khác. Trả lời kiểu "em kiểm tra lại
đi" = 0 điểm, vì nó đẩy việc về cho đội mà không cho họ thêm thông tin nào.

---

## Bài về nhà

1. Đọc lại `docs/giao-trinh/00-khung-danh-gia.md` §1 và §3 — buổi 03 vẽ kiến trúc phải đỡ được bằng chứng của G2.
2. Đọc `docs/de-bai.md` trong repo của bạn, **hết**. Buổi 03 vẽ kiến trúc cho đúng đề này — ba tầng người học / môn học / chương trình, không phải chỉ phần đề cương.
3. Mở `data/de-cuong/BUS2051-phan-tich-du-lieu.md` và `data/rubric.yaml`. **Tự chấm tay** đề cương đó theo 6 tiêu chí, hẹn đồng hồ 15 phút, ghi kết quả vào `JOURNAL.md`.
   Đối chiếu với bảng lỗi đã gài ở `data/de-cuong/README.md` — bạn tìm ra mấy lỗi trong sáu?
   Tiêu chí nào bạn chấm tay mà không ra kết luận thì ngưỡng đó chưa đủ rõ: **người không chấm nổi thì agent cũng không chấm nổi**.
4. Thêm 2 dòng `JOURNAL.md`.

---

## Tiêu chí đạt buổi 02

- [ ] Repo riêng từ template, clone về máy, có nhánh `develop`
- [ ] `pip install -r requirements.txt` xong; `make run` chạy; `curl localhost:8000/health` ra `ok`
- [ ] `git check-ignore -v .env` có kết quả và `git status` **không** thấy `.env`
- [ ] `git ls-files | grep data` thấy **4 file** — và giải thích được vì sao `git status` sạch mà vẫn có thể thiếu file
- [ ] `pre-push` hook đã cài
- [ ] `make test` ra **5 passed** sau khi thêm `pytest.ini`; `ruff check` xanh
- [ ] `JOURNAL.md` ghi **ba** chỗ lệch: lệnh cài trong README · số chương sổ tay · CI không chạy cho PR nhắm vào `develop`
- [ ] Agent đã trả lời kèm đường dẫn file, và bạn đã **tự mở file đó kiểm lại**
- [ ] PR merge vào `develop`, `gh run list` có một lần chạy thành công
- [ ] Bài tập chéo ≥ 2/3

Ô thứ năm là ô mentor hay bỏ qua nhất vì nó "chỉ là journal". Nhưng nó là ô duy nhất dạy được
thứ không giảng được: tài liệu nói một đằng, code làm một nẻo, và chỉ người đối chiếu mới thấy.
