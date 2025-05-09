import streamlit as st
from datetime import datetime
import random

# Thông tin cá nhân
ten = "Phạm Quốc Hưng"
ngay_sinh = "1983-12-21"

# Màu sắc hợp mệnh Thủy
mau_hop_menh = ["Xanh dương", "Đen", "Trắng", "Bạc"]

# Hàm sinh số may mắn
def sinh_so_may_man(ten, ngay_sinh):
    today = datetime.now().strftime("%Y-%m-%d")
    seed_str = ten.lower() + ngay_sinh + today
    random.seed(seed_str)
    return random.sample(range(1, 100), 1)

# Giao diện Streamlit
st.set_page_config(page_title="Số May Mắn Phong Thủy", page_icon="🔮", layout="centered")

st.title("🔮 Số May Mắn Hôm Nay")
st.subheader(f"Xin chào, {ten}")

if st.button("✨ Xem số may mắn hôm nay"):
    so = sinh_so_may_man(ten, ngay_sinh)
    mau = random.choice(mau_hop_menh)

    st.markdown(f"""
    ### 🎯 Số may mắn hôm nay:
    - `{so[0]}`

    ### 🎨 Màu sắc hợp mệnh:
    - **{mau}**
    """)

st.caption("✨ App phong thủy mini by ChatGPT")
