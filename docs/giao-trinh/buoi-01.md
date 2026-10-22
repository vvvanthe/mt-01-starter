# Buổi 01 — Sáu tuần, sáu cổng, sáu tiêu chí: mentor sẽ bị hỏi gì

> Nguồn của buổi này: [khung đánh giá — Gates, deliverables, rubric](00-khung-danh-gia.md)
> · đề bài: [MT-01](../de-bai.md)
> Thời lượng 120' · Trong repo dự án, hai file trên nằm ở `docs/giao-trinh/` và `docs/de-bai.md`

## Mentor xong buổi này phải làm được

- Nói đúng **không cần tra tài liệu**: tuần nào là gate nào, và bằng chứng tối thiểu của gate đó là gì.
- Chỉ ra **3 deliverable mà cohort trước thiếu nhiều nhất** và giải thích vì sao đó lại là chỗ dễ ghi điểm nhất.
- **Bắt được một câu agent nói sai** về chính repo mình vừa tạo, rồi chứng minh bằng một lệnh chạy ra số.

## Câu đội sẽ hỏi mà buổi này trả lời

1. *"Tuần này em nộp gì là đủ ạ?"*
2. *"Sản phẩm em chạy được rồi, vậy là xong chưa anh?"*
3. *"Em để AI viết gần hết code, có bị trừ điểm không?"*

## Điều kiện trước

Đã đọc [đề bài MT-01](../de-bai.md) (10 phút). Đã cài agent coding, Git, và đăng nhập
`gh`. Chưa cần Python.

---

## Slide (30 phút)

| # | Tiêu đề slide | Nội dung trên slide | Người trình bày nói gì |
|---|---|---|---|
| 1 | Mentor không phải người giỏi code nhất trong phòng | Hai việc của mentor: **ra yêu cầu** và **nghiệm thu**. Không có việc thứ ba là "viết hộ code". | Mở đầu bằng lo lắng thật của phòng: "em không biết code thì mentor kiểu gì". Trả lời ngay: 15 buổi này không dạy bạn code, dạy bạn kiểm. Người nghiệm thu nhà không cần biết trộn vữa, nhưng phải biết gõ vào tường. |
| 2 | 6 tuần, 6 cổng | Sơ đồ 6 cổng ở khung đánh giá §1: W1 G1 idea+USP → W2 G2 architecture → W3 G3 agent+tools+guardrail → W4 G4 deploy+eval → W5 G5 before/after+tổng duyệt → W6 G6 Demo Day. | Chỉ vào từng mũi tên. Nhấn: gate là **cổng**, không phải mốc báo cáo. Đội trễ G2 ba ngày thì G3 không thể đúng hạn — trễ cộng dồn, không tự khỏi. |
| 3 | Bằng chứng tối thiểu từng gate | Bảng G1–G6 ở `docs/giao-trinh/00-khung-danh-gia.md` §1, cột "bằng chứng tối thiểu" — chép nguyên văn lên slide. | Đọc chậm cột bằng chứng. Đây là câu trả lời cho câu hỏi số 1 của đội — và mentor phải thuộc để không phải hẹn "mai anh xem lại rồi trả lời". |
| 4 | At-risk triggers | Miss standup 2 ngày liên tiếp · không commit 3 ngày · gate trễ >3 ngày. | Ba trigger này là việc của mentor, không phải của BTC. Thấy trigger thì mở Playbook L1/L2/L3 bên giáo trình vận hành. |
| 5 | "Chạy được" không phải "xong" | 10 deliverables kèm vị trí trong repo (khung đánh giá §3). | Đây là câu trả lời cho câu hỏi số 2. Nhiều đội mất điểm **không phải vì code kém mà vì thiếu hồ sơ**. Nói thẳng: code chạy là điều kiện cần, hồ sơ là điều kiện đủ. |
| 6 | Ba con số phải thuộc | Video demo **thiếu 11/11 đội (100%)** · Evaluation Evidence **thiếu ~82%** · Pitch Deck **thiếu ~64%**. | Ba con số này là vũ khí coaching mạnh nhất của mentor. Đội nào làm được ba thứ này thì gần như chắc chắn vượt phần lớn các đội còn lại — mà cả ba đều **không cần code giỏi hơn**. |
| 7 | 6 tiêu chí Demo Day × 5 mức | Bảng 6 tiêu chí: Hoàn thiện sản phẩm · Kỹ thuật AI · Evaluation · UI/UX · Ý tưởng & ứng dụng thật · Pitch. Thang 9-10 Giỏi, 7-8 Khá, 5-6 TB, 3-4 Yếu, 1-2 Kém. | Nói rõ giới hạn: tên tiêu chí và mô tả mức ổn định, **trọng số có thể đổi theo cohort** — đầu mỗi cohort phải đối chiếu với bản BTC phát hành. Mentor nói chắc chắn về thứ chưa chắc là cách mất uy tín nhanh nhất. |
| 8 | Sáu sai lầm engineering | Không CI/CD · bỏ qua evaluation · README sơ sài · không có environment setup rõ · gộp hết code vào một file · không viết test. | Sáu thứ này không phải lỗi thuật toán, là lỗi nghề. Đó là lý do mentor không-biết-code vẫn phát hiện được: cả sáu đều kiểm bằng cách **mở repo ra xem**, không cần đọc logic. |
| 9 | Agent nói rất chắc về thứ nó chưa hề kiểm | Hỏi agent *"repo này có bao nhiêu file?"* và *"`make test` ra gì?"* — nó sẽ trả lời một con số và trả lời "test xanh". Sự thật: **68 file** (người dạy chạy `git ls-files | wc -l` trước buổi để lấy số đúng — số này tăng khi giáo trình thêm buổi) và **2 passed, 3 errors**. | Đây là slide quan trọng nhất của buổi. Agent không sai vì kém — nó sai vì **đoán thay vì chạy**, và nó đoán theo cái quen thuộc nhất (repo nào mà test chẳng xanh). Quy tắc của cả khoá: **câu hỏi về trạng thái repo chỉ được trả lời bằng một lệnh**. Lab bước 4 làm đúng việc này. |
| 10 | Agent là thợ, mentor là người nghiệm thu | Vòng lặp 4 bước: *ra yêu cầu rõ → agent làm → **mentor chạy phép kiểm** → sửa yêu cầu*. Bỏ bước 3 thì ba bước còn lại vô nghĩa. | Trả lời câu hỏi số 3 của đội: dùng AI viết code **không** bị trừ điểm; không kiểm được thứ AI viết mới bị trừ. Suốt 15 buổi, mỗi bài thực hành đều có một phép kiểm — đó là phần được chấm. |
| 11 | Đề xuyên suốt: MT-01 — ba tầng | **Hệ thống AI agent chuẩn hóa chất lượng đào tạo đại học** (case TTN–UEH). **A. Người học**: hỏi đáp grounded + hỗ trợ ESL. **B. Môn học**: rubric 6 tiêu chí, giảng viên duyệt. **C. Chương trình**: số tổng hợp ẩn danh. | Giới thiệu đề, và nói rõ nó **không chỉ là rà đề cương** — đó là tầng B. Ba tầng nối nhau: bản đã duyệt ở B mới là nguồn cho A, số liệu từ B lên C. Ta build thật, deploy thật, eval thật; cuối 15 buổi mỗi mentor có repo đi đủ G1→G6. |
| 12 | Scope guard — thứ MT-01 cố tình không làm | Không LMS thật · không chấm điểm sinh viên · không multi-agent · không fine-tune · không Next.js ở bản cơ bản. | Đọc to danh sách này và dán lên tường. Mentor sẽ phải nói đúng câu này với đội của mình vào tuần 3, khi đội muốn thêm tính năng thay vì hoàn thiện cái đang có. |

---

## Thực hành (60 phút) — Lái agent lần đầu, và bắt nó nói sai

**Sau lab, repo MT-01 có:** repo riêng từ template, `docs/00-ban-do-khoa.md` điền xong,
`JOURNAL.md` dòng đầu tiên, và một ghi chép về chỗ agent đã nói sai.

### Bước 1 — Lấy repo riêng từ template (8')

Người dạy đã đưa repo mẫu lên org của khoá. Bạn **không** tự dựng cây thư mục — bấm một nút.

```
1. Mở https://github.com/<ORG>/mt-01-starter
2. Bấm "Use this template" → "Create a new repository"
3. Tên: mt-01-<tên-bạn> · chọn Private · Create
```

Clone về **đâu cũng được** — giáo trình và đề bài nằm sẵn trong repo:

```bash
gh repo clone <TÊN-BẠN>/mt-01-<tên-bạn>
cd mt-01-<tên-bạn>
ls docs/giao-trinh/ docs/de-bai.md   # thấy hai thứ này là clone đủ
```

**Phép kiểm:** `gh repo view --json name,visibility,isTemplate` — repo của bạn, Private, và
`isTemplate: false` (template là repo gốc, không phải repo của bạn).
Chi tiết ở [repo-mau/README.md](repo-mau/README.md) phần "Học viên".

### Bước 2 — Đọc đề bài và xem khung mình sẽ sống trong đó 6 tuần (12')

**Chưa cài gì cả.** Dựng môi trường là buổi 02; hôm nay chỉ đọc.

```bash
# De bai day du — doc het, 10 phut
cat docs/de-bai.md | head -60

# Giao trinh va khung danh gia nam trong repo
ls docs/giao-trinh/

# Ba file deliverable da co san, chi can dien
ls ARCHITECTURE.md JOURNAL.md WORKLOG.md
```

**Đạt khi** bạn trả lời được ba câu, không mở lại file:
1. Hệ thống MT-01 có **mấy tầng**, và chuẩn hóa đề cương là tầng nào?
2. Ba ràng buộc nào khiến đề này **không phải** một chatbot bọc API?
3. Thư mục nào trong repo ứng với deliverable số 10 — thứ 82% đội cohort trước bỏ trống?

Câu một hay trả lời sai thành "hệ thống rà đề cương". Đề có **ba tầng**: trợ lý người học
(hỏi đáp grounded + hỗ trợ ESL), chuẩn hóa môn học (rubric 6 tiêu chí + giảng viên duyệt), và
bức tranh chương trình (số tổng hợp ẩn danh). Rà đề cương là tầng giữa.

### Bước 3 — Bản đồ khoá: bạn viết trước, agent viết sau (15')

Mở một file nháp và **tự tay** điền bảng này trước, không mở sổ tay:

| Tuần | Gate | Bằng chứng tối thiểu | Buổi của khoá |
|---|---|---|---|

Điền xong 6 dòng rồi mới gửi prompt:
```
Đọc docs/giao-trinh/00-khung-danh-gia.md mục 1 và mục 2. Viết docs/00-ban-do-khoa.md gồm bảng
6 dòng: Tuần | Gate | Bằng chứng tối thiểu | Buổi của khoá. Trích nguyên văn cột bằng chứng,
không diễn giải lại. Cuối file thêm mục "At-risk triggers" cũng trích nguyên văn.
```

**Phép kiểm:**
```bash
diff <(sed -n '/^|/p' nhap.md) <(sed -n '/^|/p' docs/00-ban-do-khoa.md)
```
**Đạt khi:** bạn **đọc được** mọi chỗ lệch và nói được ai đúng. Lệch không phải lỗi — lệch mà
không biết ai đúng mới là lỗi. Chỗ bạn nhớ sai hôm nay chính là chỗ đội sẽ hỏi tuần sau.

### Bước 4 — Gài bẫy agent (20') ⭐ bài tập cốt lõi của buổi

Hỏi agent đúng ba câu sau, **theo thứ tự này**, mỗi câu một lượt riêng. Hai câu đầu hỏi về
**trạng thái repo** — đây là chỗ agent hay đoán nhất. Câu ba hỏi về **nội dung tài liệu** — chỗ
agent trả lời được, nếu nó chịu mở file.

```
1. Repo này có bao nhiêu file đang được git theo dõi? Trả lời bằng một số.
2. Nếu tôi chạy `make test` bây giờ thì ra kết quả gì?
3. Deliverable nào mà 100% đội cohort trước đều thiếu? Trỏ đúng file và mục trong repo.
```

Với **từng** câu trả lời, chạy phép kiểm của riêng nó:

```bash
# Câu 1 — đếm, đừng tin. (Đừng dùng ls: nó không biết git theo dõi gì.)
git ls-files | wc -l

# Câu 2 — chạy thật. Buổi 02 mới dựng môi trường, nên hôm nay chỉ cần chạy và xem dòng cuối cùng
#          của phần tổng kết pytest. Chưa có venv thì ghi lại nguyên văn lỗi, cũng là một kết quả.
make test

# Câu 3 — con số 100% nằm ở đâu trong repo?
grep -rn "11/11" docs/giao-trinh/
```

**Đạt khi:** bạn ghi vào `JOURNAL.md` theo mẫu — mỗi câu một dòng:

```
2026-10-21 · Câu 2: agent trả lời "test sẽ pass hết". SAI. Chạy thật: 2 passed, 3 errors.
  Nguyên nhân: agent đoán theo cái quen thuộc, không chạy lệnh nào.
  Bài học: câu hỏi về trạng thái repo phải trả lời bằng lệnh — ở đây là make test.
```

**Điều quan trọng nhất của buổi học nằm ở đây.** Agent nói sai với giọng rất chắc chắn, và nó sai
**vì đoán thay vì chạy** — không phải vì kém. Đội của bạn sẽ nhận đúng kiểu câu trả lời này hàng
ngày: tự tin, hợp lý, và không ai kiểm. Mentor phân biệt được "agent đã chạy và báo lại" với
"agent đoán rồi nói như đã chạy" thì coaching được; không phân biệt được thì chỉ biết nói "em
kiểm tra lại đi".

> Nếu agent của bạn cẩn thận và tự chạy lệnh trước khi trả lời (bản mới hay làm vậy): vẫn làm
> bước này, nhưng **ghi lại lệnh nó đã chạy** rồi tự chạy lại và so kết quả. Và hỏi thêm *"con số
> 82% thiếu Evaluation Evidence lấy ở file nào, mục nào?"* rồi mở đúng mục đó ra đối chiếu. Mục
> tiêu là **thói quen đòi nguồn và đòi lệnh**, không phải bắt agent sai.

### Bước 5 — Commit đầu tiên (10')

```bash
git checkout -b develop
git add -A && git commit -m "chore: cay thu muc + ban do khoa + journal ngay 1"
git push -u origin develop
```
**Phép kiểm:** `git log --oneline` có 1 commit; `gh repo view --web` thấy branch `develop`.
**Đạt khi:** `JOURNAL.md` đã có nội dung **từ ngày đầu**. Deliverable #8 là thứ không thể
viết bù vào tuần 6 — journal viết lùi ngày thì nhìn ra ngay.

---

## Bài tập chéo (20 phút) — Đổi vai, 15 phút breakout

Ghép cặp. A làm **trưởng đội tuần 1**, B làm **mentor**. Sau 15' đổi vai.

**A nói đúng ba câu này (đọc nguyên văn, đừng diễn thêm):**
1. *"Nhóm em chốt đề rồi, tuần này em dựng Docker với CI trước cho chắc."*
2. *"Em chạy thử thấy agent trả lời ổn, nên em bỏ phần eval để dành thời gian làm thêm 2 tính năng."*
3. *"Anh code hộ em cái API nhỏ này được không, em bị kẹt 2 ngày rồi."*

**B phải làm được ba việc:**
- Với câu 1: chỉ ra đội đang ở **cổng G1**, chưa qua G2, và hỏi *"đã có 5 user thật xem prototype chưa?"* trước khi đồng ý cho dựng hạ tầng.
- Với câu 2: trả lời bằng **con số 82%**, không bằng lời khuyên chung. Và hỏi *"ổn là bao nhiêu phần trăm, trên bộ test nào?"*
- Với câu 3: **từ chối viết code hộ**, và đổi thành một câu hỏi mở về chỗ kẹt. Viết code hộ đội là cách nhanh nhất để tuần 6 đội không bảo vệ được sản phẩm của chính mình.

**Chấm:** mỗi việc làm được 1 điểm. B dưới 2/3 thì làm lại với cặp khác.

---

## Bài về nhà

1. Đọc hết [`docs/de-bai.md`](../de-bai.md) và [khung đánh giá](00-khung-danh-gia.md). Đọc hết, không skim — buổi 02 trở đi mọi phép kiểm đều trỏ về hai file này.
2. **Cài sẵn Python 3.12 (hoặc 3.11)** và kiểm bằng `python3 --version`. Buổi 02 dựng môi trường; ai chưa cài được thì mất nửa buổi.
3. Viết nháp **5 use case** của MT-01: 5 nhóm người cụ thể + việc cụ thể họ cần làm. Chưa cần chọn, chỉ cần liệt kê — buổi 05 dùng lại danh sách này.
4. Thêm 2 dòng nữa vào `JOURNAL.md`.

---

## Tiêu chí đạt buổi 01

- [ ] Repo riêng tạo từ template, clone về máy, có branch `develop`
- [ ] Nói được MT-01 có **ba tầng** và ba ràng buộc khiến nó không phải chatbot bọc API
- [ ] `docs/00-ban-do-khoa.md` có bảng 6 gate, cột bằng chứng trích nguyên văn
- [ ] `JOURNAL.md` ghi ≥1 chỗ agent nói sai về trạng thái repo, kèm **nguyên nhân** và **lệnh đã chạy**
- [ ] Nói được 6 gate + 3 con số (100% / 82% / 64%) mà không mở tài liệu
- [ ] Bài tập chéo đạt ≥2/3

Không đạt ô thứ tư thì **không sang buổi 02**. Bốn ô còn lại là thủ tục; ô thứ tư là nghề.
