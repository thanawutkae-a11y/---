// --- ข้อมูลรายการอาหาร (Food Items Data) ---
const menuData = [
{
id: 1,
title: "ผัดไทกุ้งสด",
category: "padthai",
price: 60,
desc: "ผัดไทเส้นเหนียวนุ่ม ผัดซอสเข้มข้น เสิร์ฟพร้อมกุ้งสดตัวโต",
image: "https://images.unsplash.com/photo-1559847844-5315695dadae?auto=format&fit=crop&w=600&q=80"
},
{
id: 2,
title: "ผัดไทโบราณ / ห่อไข่",
category: "padthai",
price: 50,
desc: "ผัดไทสูตรดั้งเดิม หอมกลิ่นกระทะ เสิร์ฟพร้อมเครื่องเคียงครบครัน",
image: "https://images.unsplash.com/photo-1626804475297-41608e074eb1?auto=format&fit=crop&w=600&q=80"
},
{
id: 3,
title: "กะเพราหมูกรอบ (ราดข้าว)",
category: "kaprao",
price: 55,
desc: "หมูกรอบแท้ หนังกรอบเนื้อนุ่ม ผัดกะเพราแห้งรสจัดจ้าน",
image: "https://images.unsplash.com/photo-1589301760014-d929f3979dbc?auto=format&fit=crop&w=600&q=80"
},
{
id: 4,
title: "กะเพราเนื้อสับ (ราดข้าว)",
category: "kaprao",
price: 60,
desc: "เนื้อสับอย่างดี ผัดกะเพราแท้หอมเข้มข้น ไม่ใส่ผักเจือปน",
image: "https://images.unsplash.com/photo-1563379091339-03b21ab4a4f8?auto=format&fit=crop&w=600&q=80"
},
{
id: 5,
title: "กะเพราหมูสับ / ไก่ (ราดข้าว)",
category: "kaprao",
price: 45,
desc: "เมนูฮิตตลอดกาล รสชาติเข้มข้น หอมใบกะเพราสด",
image: "https://images.unsplash.com/photo-1603133872878-684f208fb84b?auto=format&fit=crop&w=600&q=80"
},
{
id: 6,
title: "ไข่ดาวขอบกรอบ",
category: "extra",
price: 10,
desc: "ไข่ดาวทอดขอบกรอบ ไข่แดงเยิ้มกำลังดี",
image: "https://images.unsplash.com/photo-1525351484163-7529414344d8?auto=format&fit=crop&w=600&q=80"
},
{
id: 7,
title: "ไข่เจียวทรงเครื่อง",
category: "extra",
price: 15,
desc: "ไข่เจียวฟูนุ่ม เพิ่มความอร่อยเมื่อทานคู่กะเพรา",
image: "https://images.unsplash.com/photo-1510693206972-df098062cb71?auto=format&fit=crop&w=600&q=80"
}
];

// --- ตัวแปรสำหรับระบบ Cart ---
let cart = [];

// --- เมื่อโหลดหน้าเว็บ ---
document.addEventListener("DOMContentLoaded", () => {
renderMenu(menuData);
});

// --- แสดงรายการอาหาร ---
function renderMenu(items) {
const grid = document.getElementById("menu-grid");
grid.innerHTML = "";

items.forEach(item => {
    const card = document.createElement("div");
    card.className = "menu-card";
    card.innerHTML = `
        <img src="${item.image}" alt="${item.title}" class="menu-img">
        <div class="menu-info">
            <h3 class="menu-title">${item.title}</h3>
            <p class="menu-desc">${item.desc}</p>
            <div class="menu-bottom">
                <span class="price">${item.price} ฿</span>
                <button class="add-cart-btn" onclick="addToCart(${item.id})">
                    <i class="fa-solid fa-plus"></i> เพิ่มสั่ง
                </button>
            </div>
        </div>
    `;
    grid.appendChild(card);
});


}

// --- กรองหมวดหมู่เมนู ---
function filterMenu(category, btn) {
// เปลี่ยนสถานะปุ่ม Active
const buttons = document.querySelectorAll(".cat-btn");
buttons.forEach(b => b.classList.remove("active"));
btn.classList.add("active");

// กรองข้อมูล
if (category === "all") {
    renderMenu(menuData);
} else {
    const filtered = menuData.filter(item => item.category === category);
    renderMenu(filtered);
}


}

// --- ระบบ ตะกร้าสินค้า ---
function addToCart(id) {
const product = menuData.find(item => item.id === id);
if (product) {
cart.push(product);
updateCartUI();
}
}

function updateCartUI() {
// อัปเดตจำนวนตัวเลขตรงตะกร้า
document.getElementById("cart-count").innerText = cart.length;

// แสดงรายการใน Modal
const cartItemsContainer = document.getElementById("cart-items");
cartItemsContainer.innerHTML = "";

let total = 0;

if (cart.length === 0) {
    cartItemsContainer.innerHTML = "<p style='text-align:center; color:#6b7280;'>ยังไม่มีรายการในตะกร้า</p>";
} else {
    cart.forEach((item, index) => {
        total += item.price;
        const itemDiv = document.createElement("div");
        itemDiv.className = "cart-item";
        itemDiv.innerHTML = `
            <div>
                <div class="cart-item-title">${item.title}</div>
                <div class="cart-item-price">${item.price} บาท</div>
            </div>
            <button onclick="removeFromCart(${index})" style="background:none; border:none; color:#ef4444; cursor:pointer;">
                <i class="fa-solid fa-trash"></i>
            </button>
        `;
        cartItemsContainer.appendChild(itemDiv);
    });
}

document.getElementById("cart-total-price").innerText = total + " บาท";


}

function removeFromCart(index) {
cart.splice(index, 1);
updateCartUI();
}

function toggleCartModal() {
const modal = document.getElementById("cart-modal");
modal.classList.toggle("active");
}

function checkout() {
if (cart.length === 0) {
alert("กรุณาเลือกรายการอาหารก่อนทำการสั่งซื้อครับ");
return;
}

let summary = "รายการสั่งซื้อ:\n";
let total = 0;
cart.forEach((item, i) => {
    summary += `${i + 1}. ${item.title} - ${item.price} บาท\n`;
    total += item.price;
});
summary += `\nราคารวมทั้งสิ้น: ${total} บาท\n\nต้องการโทรสั่งอาหารที่เบอร์ 081-234-5678 เลยหรือไม่?`;

if (confirm(summary)) {
    window.location.href = "tel:0812345678";
}


}

// --- Toggle เมนูบนมือถือ ---
function toggleMobileNav() {
const nav = document.getElementById("nav-links");
nav.classList.toggle("active");
}
