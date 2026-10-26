// ============================================================
// CẤU HÌNH
// ============================================================
var SHEET_URL = "https://script.google.com/macros/s/AKfycbxMMy92Pm6g7Bw9-XbQD79z9pwPRZOo8KuRg3GlK1jjD-cuO7zaK5iCGiPfB_33EdoX/exec";
var dangGui = false;

// ============================================================
// 1. KIỂM TRA GIÁ
// ============================================================
function matchPrice(price, range) {
    if (range === "all") return true;
    if (range === "under3") return price < 3000000;
    if (range === "3to4") return price >= 3000000 && price <= 4000000;
    if (range === "over4") return price > 4000000;
    return true;
}

// ============================================================
// 2. TIỀN TỆ
// ============================================================
function parseMoney(str) {
    if (typeof str === "number") return str;
    if (!str) return 0;
    var clean = String(str).replace(/[^\d]/g, "");
    return Number(clean) || 0;
}

function formatMoney(num) {
    num = Number(num) || 0;
    if (num < 0) num = 0;
    return num.toLocaleString("vi-VN") + " VNĐ";
}

// ============================================================
// 3. CHỐNG XSS
// ============================================================
function escapeHtml(str) {
    return String(str)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&#39;");
}

// ============================================================
// 4. LIGHTBOX — BẤM ẢNH PHÓNG TO
// ============================================================
function phongToAnh(img) {
    var lightbox = document.getElementById("lightbox");
    var lightboxImg = document.getElementById("lightbox-img");
    if (lightbox == null || lightboxImg == null) return;

    lightboxImg.src = img.src;
    lightboxImg.alt = img.alt;
    lightbox.className = "lightbox active";   // đổi class trực tiếp
}

function dongAnh() {
    var lightbox = document.getElementById("lightbox");
    if (lightbox == null) return;
    lightbox.className = "lightbox";          // bỏ active
}

// ============================================================
// 5. TÍNH TỔNG TIỀN
// ============================================================
function tinhTongTien() {
    var form = document.frmDangKy;
    if (!form) return;

    var tongGiaTour = 0;
    var chk = form.chkTour;

    // checkbox có thể là 1 phần tử hoặc nhiều phần tử
    if (chk.length == undefined) {
        if (chk.checked) tongGiaTour = Number(chk.value) || 0;
    } else {
        for (var i = 0; i < chk.length; i++) {
            if (chk[i].checked) {
                tongGiaTour += Number(chk[i].value) || 0;
            }
        }
    }

    var nguoiLon = parseInt(form.soluong.value, 10) || 0;
    var treEm = parseInt(form.treem.value, 10) || 0;
    if (nguoiLon < 0) nguoiLon = 0;
    if (treEm < 0) treEm = 0;

    var tong = tongGiaTour * nguoiLon + tongGiaTour * treEm * 0.5;

    var voucher = form.voucher.value.trim().toUpperCase();
    if (voucher == "GIAM100" && tong > 0) tong = tong - 100000;

    if (tong < 0) tong = 0;
    tong = Math.round(tong);

    form.tongtien.value = formatMoney(tong);
}

// ============================================================
// 6. TĂNG / GIẢM SỐ LƯỢNG
// ============================================================
function tangSoLuong(id) {
    var input = document.getElementById(id);
    if (input == null) return;
    var n = parseInt(input.value, 10) || 0;
    input.value = n + 1;
    tinhTongTien();
}

function giamSoLuong(id) {
    var input = document.getElementById(id);
    if (input == null) return;
    var n = parseInt(input.value, 10) || 0;
    var min = (id == "soluong") ? 1 : 0;
    if (n > min) input.value = n - 1;
    tinhTongTien();
}

// ============================================================
// 7. ĐĂNG KÝ TOUR
// ============================================================
function dangKyTour() {
    var form = document.frmDangKy;
    if (!form) return false;

    var ten = form.txtTen.value.trim();
    var sdt = form.txtSDT.value.trim();

    if (ten == "") {
        alert("Vui lòng nhập tên khách hàng!");
        form.txtTen.focus();
        return false;
    }
    if (sdt == "") {
        alert("Vui lòng nhập số điện thoại!");
        form.txtSDT.focus();
        return false;
    }
    if (!/^\d{10,11}$/.test(sdt)) {
        alert("Số điện thoại phải là 10 hoặc 11 chữ số!");
        form.txtSDT.focus();
        return false;
    }

    var soLuong = parseInt(form.soluong.value, 10);
    if (isNaN(soLuong) || soLuong <= 0) {
        alert("Số lượng vé phải là số nguyên dương!");
        form.soluong.focus();
        return false;
    }

    // thu thập tour đã tick
    var dsMaTour = [];
    var dsTenTour = [];
    var chk = form.chkTour;

    if (chk.length == undefined) {
        if (chk.checked) {
            dsMaTour.push(chk.getAttribute("data-ma") || "");
            dsTenTour.push(chk.getAttribute("data-ten") || chk.value);
        }
    } else {
        for (var i = 0; i < chk.length; i++) {
            if (chk[i].checked) {
                dsMaTour.push(chk[i].getAttribute("data-ma") || "");
                dsTenTour.push(chk[i].getAttribute("data-ten") || chk[i].value);
            }
        }
    }

    if (dsMaTour.length == 0) {
        alert("Vui lòng chọn ít nhất một tour!");
        return false;
    }

    tinhTongTien();
    var tongTien = parseMoney(form.tongtien.value);

    // tạo đối tượng giao dịch
    var gd = {
        tenKhach: ten,
        sdtKhach: sdt,
        maTour: dsMaTour.join(", "),
        tenTour: dsTenTour.join(", "),
        soLuongVe: soLuong,
        treEm: parseInt(form.treem.value, 10) || 0,
        ghiChu: form.ghichu.value.trim(),
        voucher: form.voucher.value.trim(),
        tongTien: tongTien,
        thoiGian: new Date().toLocaleString("vi-VN")
    };

    // lưu localStorage
    var dsCu = JSON.parse(localStorage.getItem("lichSuGiaoDich")) || [];
    dsCu.push(gd);
    localStorage.setItem("lichSuGiaoDich", JSON.stringify(dsCu));

    // gửi Google Sheet
    guiLenGoogleSheet(gd);

    alert(
        "ĐĂNG KÝ TOUR THÀNH CÔNG!\n" +
        "Khách hàng: " + ten + "\n" +
        "SĐT: " + sdt + "\n" +
        "Tổng tiền: " + formatMoney(tongTien)
    );
    return true;
}

// ============================================================
// 8. GỬI GOOGLE SHEET
// ============================================================
function guiLenGoogleSheet(gd) {
    dangGui = true;
    fetch(SHEET_URL, {
        method: "POST",
        mode: "no-cors",
        headers: { "Content-Type": "text/plain;charset=utf-8" },
        body: JSON.stringify(gd)
    })
    .then(function () {
        console.log("Đã gửi Google Sheet.");
        dangGui = false;
    })
    .catch(function (err) {
        console.error("Lỗi gửi Google Sheet:", err);
        dangGui = false;
    });
}

// ============================================================
// 9. LỊCH SỬ GIAO DỊCH
// ============================================================

// Biến lưu toàn bộ lịch sử gốc (đọc từ localStorage)
var toanBoLichSu = [];

// Đọc lịch sử từ localStorage vào biến toàn cục
function docLichSuGoc() {
    try {
        toanBoLichSu = JSON.parse(localStorage.getItem("lichSuGiaoDich")) || [];
        if (!Array.isArray(toanBoLichSu)) toanBoLichSu = [];
    } catch (e) {
        console.error("Lỗi đọc lịch sử:", e);
        toanBoLichSu = [];
    }
}

// Hiển thị lịch sử — nhận danh sách tùy chọn
function hienThiLichSu(danhSach) {
    var ketQua = document.getElementById("ketQua");
    if (!ketQua) return;

    // Nếu không truyền vào thì đọc từ localStorage (giữ tương thích cũ)
    if (typeof danhSach === "undefined") {
        docLichSuGoc();
        danhSach = toanBoLichSu.slice();
    }

    if (!danhSach || danhSach.length == 0) {
        ketQua.innerHTML = "<p class='thong-bao-rong'>Chưa có giao dịch nào.</p>";
        return;
    }

    // đảo ngược để mới nhất lên đầu (không đổi mảng gốc)
    var ds = danhSach.slice().reverse();

    var html = "<table>";
    html += "<tr><th>STT</th><th>Tên khách</th><th>SĐT</th>";
    html += "<th>Mã tour</th><th>Tên tour</th><th>Người lớn</th>";
    html += "<th>Trẻ em</th><th>Voucher</th><th>Tổng tiền</th><th>Thời gian</th></tr>";

    for (var i = 0; i < ds.length; i++) {
        var gd = ds[i];
        html += "<tr>";
        html += "<td>" + (i + 1) + "</td>";
        html += "<td>" + escapeHtml(gd.tenKhach || "") + "</td>";
        html += "<td>" + escapeHtml(gd.sdtKhach || "") + "</td>";
        html += "<td>" + escapeHtml(gd.maTour || "—") + "</td>";
        html += "<td>" + escapeHtml(gd.tenTour || "—") + "</td>";
        html += "<td>" + (gd.soLuongVe || 0) + "</td>";
        html += "<td>" + (gd.treEm || 0) + "</td>";
        html += "<td>" + escapeHtml(gd.voucher || "—") + "</td>";
        html += "<td>" + formatMoney(gd.tongTien) + "</td>";
        html += "<td>" + escapeHtml(gd.thoiGian || "") + "</td>";
        html += "</tr>";
    }
    html += "</table>";
    ketQua.innerHTML = html;
}

function xoaLichSu() {
    if (confirm("Bạn có chắc muốn xóa toàn bộ lịch sử giao dịch?")) {
        localStorage.removeItem("lichSuGiaoDich");
        toanBoLichSu = [];
        hienThiLichSu();
        datLaiLocNgay();
        alert("Đã xóa toàn bộ lịch sử!");
    }
}

// ============================================================
// 9b. BỘ LỌC NGÀY CHO TRANG LỊCH SỬ
// ============================================================

// Lấy đối tượng Date từ một giao dịch (hỗ trợ nhiều tên trường)
function layNgayGiaoDich(gd) {
    if (!gd) return null;
    var raw = gd.thoiGian || gd.ngay || gd.date || gd.createdAt || gd.time;
    if (!raw) return null;

    // thoiGian lưu dạng "dd/mm/yyyy, hh:mm:ss" (toLocaleString vi-VN)
    // -> chuyển về Date an toàn
    var d = null;
    if (typeof raw === "string") {
        // thử parse trực tiếp trước
        d = new Date(raw);

        // nếu fail, thử tách theo định dạng vi-VN dd/mm/yyyy
        if (isNaN(d.getTime())) {
            var m = raw.match(/^(\d{1,2})\/(\d{1,2})\/(\d{4})/);
            if (m) {
                d = new Date(Number(m[3]), Number(m[2]) - 1, Number(m[1]));
            }
        }
    } else {
        d = new Date(raw);
    }

    return (d && !isNaN(d.getTime())) ? d : null;
}

// Định dạng Date -> yyyy-mm-dd cho input[type=date]
function dinhDangNgayInput(date) {
    var y = date.getFullYear();
    var m = String(date.getMonth() + 1).padStart(2, "0");
    var d = String(date.getDate()).padStart(2, "0");
    return y + "-" + m + "-" + d;
}

// Định dạng yyyy-mm-dd -> dd/mm/yyyy để hiển thị
function dinhDangNgayHienThi(str) {
    if (!str) return "";
    var parts = str.split("-");
    if (parts.length != 3) return str;
    return parts[2] + "/" + parts[1] + "/" + parts[0];
}

// Áp dụng lọc theo khoảng ngày
function apDungLocNgay() {
    var tuStr = document.getElementById("tuNgay").value;
    var denStr = document.getElementById("denNgay").value;

    if (!tuStr || !denStr) {
        alert('Vui lòng chọn cả "Từ ngày" và "Đến ngày" để lọc.');
        return;
    }

    var tu = new Date(tuStr + "T00:00:00");
    var den = new Date(denStr + "T23:59:59");

    if (tu > den) {
        alert('"Từ ngày" phải nhỏ hơn hoặc bằng "Đến ngày".');
        return;
    }

    var ketQuaLoc = [];
    for (var i = 0; i < toanBoLichSu.length; i++) {
        var d = layNgayGiaoDich(toanBoLichSu[i]);
        if (d && d >= tu && d <= den) {
            ketQuaLoc.push(toanBoLichSu[i]);
        }
    }

    hienThiLichSu(ketQuaLoc);

    // Hiển thị tóm tắt số lượng tour đăng ký
    document.getElementById("tomTatLoc").innerHTML =
        "Trong khoảng <b>" + dinhDangNgayHienThi(tuStr) + "</b> đến <b>" +
        dinhDangNgayHienThi(denStr) + "</b>: đăng ký <b>" +
        ketQuaLoc.length + "</b> tour.";
}

// Đặt lại bộ lọc
function datLaiLocNgay() {
    var tu = document.getElementById("tuNgay");
    var den = document.getElementById("denNgay");
    var tomTat = document.getElementById("tomTatLoc");

    if (tu) tu.value = "";
    if (den) den.value = "";
    if (tomTat) tomTat.textContent = "";

    hienThiLichSu(toanBoLichSu);
}

// ============================================================
// 10. LỌC TOUR TRANG CHỦ
// ============================================================
function locTourTrangChu() {
    var region = document.getElementById("filter-region").value;
    var price = document.getElementById("filter-price").value;
    var searchEl = document.getElementById("search-tour-home");
    var keyword = searchEl ? searchEl.value.toLowerCase().trim() : "";

    var cards = document.querySelectorAll(".tour-card");
    var visible = 0;

    for (var i = 0; i < cards.length; i++) {
        var card = cards[i];
        var cardRegion = card.getAttribute("data-region");
        var cardPrice = Number(card.getAttribute("data-price"));
        var cardText = card.textContent.toLowerCase();

        var okRegion = (region == "all" || cardRegion == region);
        var okPrice = matchPrice(cardPrice, price);
        var okSearch = (keyword == "" || cardText.indexOf(keyword) > -1);

        if (okRegion && okPrice && okSearch) {
            card.style.display = "";
            visible++;
        } else {
            card.style.display = "none";
        }
    }
}

// ============================================================
// 11. LỌC TOUR TRANG ĐĂNG KÝ
// ============================================================
function locTourDangKy() {
    var region = document.getElementById("filter-region").value;
    var price = document.getElementById("filter-price").value;
    var searchEl = document.getElementById("search-tour");
    var keyword = searchEl ? searchEl.value.toLowerCase().trim() : "";

    var options = document.querySelectorAll(".tour-option");
    var visible = 0;

    for (var i = 0; i < options.length; i++) {
        var opt = options[i];
        var optRegion = opt.getAttribute("data-region");
        var optPrice = Number(opt.getAttribute("data-price"));
        var optText = opt.textContent.toLowerCase();

        var okRegion = (region == "all" || optRegion == region);
        var okPrice = matchPrice(optPrice, price);
        var okSearch = (keyword == "" || optText.indexOf(keyword) > -1);

        if (okRegion && okPrice && okSearch) {
            opt.style.display = "flex";
            visible++;
        } else {
            opt.style.display = "none";
            var chk = opt.querySelector("input[type='checkbox']");
            if (chk && chk.checked) chk.checked = false;
        }
    }

    var empty = document.getElementById("tour-empty");
    if (empty) empty.style.display = (visible == 0) ? "block" : "none";
    tinhTongTien();
}

// ============================================================
// 12. KHỞI TẠO KHI TRANG LOAD
// ============================================================
window.onload = function () {

    // --- Trang đăng ký ---
    var form = document.frmDangKy;
    if (form) {
        // gắn sự kiện tính tiền cho checkbox
        var checkboxes = document.querySelectorAll(".tour-checkbox");
        for (var i = 0; i < checkboxes.length; i++) {
            checkboxes[i].onchange = tinhTongTien;
        }

        var voucherEl = document.getElementById("voucher");
        if (voucherEl) voucherEl.oninput = tinhTongTien;

        // submit
        form.onsubmit = function (e) {
            e.preventDefault();
            if (dangGui) return;
            if (dangKyTour()) {
                form.tongtien.value = "0 VNĐ";
                form.soluong.value = "1";
                form.treem.value = "0";
            }
        };

        // reset
        form.onreset = function () {
            setTimeout(function () {
                form.tongtien.value = "0 VNĐ";
                form.soluong.value = "1";
                form.treem.value = "0";
            }, 0);
        };

        // lọc tour trang đăng ký
        if (document.getElementById("filter-region")) {
            document.getElementById("filter-region").onchange = locTourDangKy;
            document.getElementById("filter-price").onchange = locTourDangKy;
            var st = document.getElementById("search-tour");
            if (st) st.oninput = locTourDangKy;
            var rb = document.getElementById("btn-reset");
            if (rb) rb.onclick = function () {
                document.getElementById("filter-region").value = "all";
                document.getElementById("filter-price").value = "all";
                if (st) st.value = "";
                locTourDangKy();
            };
        }
    }

    // --- Trang chủ: lọc tour ---
    if (document.getElementById("filter-region") && document.querySelector(".tour-card")) {
        document.getElementById("filter-region").onchange = locTourTrangChu;
        document.getElementById("filter-price").onchange = locTourTrangChu;
        var sh = document.getElementById("search-tour-home");
        if (sh) sh.oninput = locTourTrangChu;
        var rh = document.getElementById("btn-reset");
        if (rh) rh.onclick = function () {
            document.getElementById("filter-region").value = "all";
            document.getElementById("filter-price").value = "all";
            if (sh) sh.value = "";
            locTourTrangChu();
        };
    }

    // --- Trang lịch sử ---
    if (document.getElementById("ketQua")) {
        docLichSuGoc();
        hienThiLichSu(toanBoLichSu);

        var btnLoc = document.getElementById("btnLoc");
        var btnDatLai = document.getElementById("btnDatLai");
        var btnXoa = document.getElementById("btnXoaLichSu");

        if (btnLoc) btnLoc.onclick = apDungLocNgay;
        if (btnDatLai) btnDatLai.onclick = datLaiLocNgay;
        if (btnXoa) btnXoa.onclick = xoaLichSu;
    }

    // --- Phím Esc đóng lightbox ---
    document.onkeydown = function (e) {
        if (e.key == "Escape") dongAnh();
    };
};
