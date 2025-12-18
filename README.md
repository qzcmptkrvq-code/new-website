import streamlit as st

# Page config
st.set_page_config(
    page_title="Delicious Bites Restaurant",
    page_icon="🍽️",
    layout="wide"
)

# ---------- CUSTOM CSS ----------
st.markdown("""
<style>

/* Background */
.stApp {
    background: linear-gradient(120deg, #fff5e6, #ffe0b2);
    animation: fadeIn 1.5s ease-in;
}

/* Fade animation */
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

/* Header animation */
.header {
    text-align: center;
    animation: slideDown 1.5s ease;
}

@keyframes slideDown {
    from { transform: translateY(-50px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
}

/* Card style */
.card {
    background: white;
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    transition: transform 0.3s ease;
}

.card:hover {
    transform: scale(1.05);
}

/* Button animation */
.stButton>button {
    background: #ff7043;
    color: white;
    border-radius: 20px;
    padding: 10px 25px;
    font-size: 16px;
    transition: all 0.3s ease;
}

.stButton>button:hover {
    background: #e64a19;
    transform: translateY(-3px);
}

</style>
""", unsafe_allow_html=True)

# ---------- HEADER ----------
st.markdown("""
<div class="header">
    <h1>🍽️ Delicious Bites</h1>
    <h3>Fresh • Tasty • Affordable</h3>
</div>
""", unsafe_allow_html=True)

st.markdown("---")

# ---------- NAVIGATION ----------
menu = st.sidebar.radio(
    "📍 Navigate",
    ["Home", "Menu", "Reservations", "Contact"]
)

# ---------- HOME ----------
if menu == "Home":
    st.image(
        "https://images.unsplash.com/photo-1555992336-03a23c2c9b1b",
        use_container_width=True
    )

    st.markdown("""
    <div class="card">
        <h2>Welcome to Delicious Bites!</h2>
        <p>
        Enjoy mouth-watering dishes prepared with love and the finest ingredients.
        Our cozy ambiance and friendly staff make every visit special.
        </p>
    </div>
    """, unsafe_allow_html=True)

    col1, col2, col3 = st.columns(3)
    col1.metric("⭐ Rating", "4.8 / 5")
    col2.metric("🍽️ Dishes", "50+")
    col3.metric("😊 Customers", "10k+")

# ---------- MENU ----------
elif menu == "Menu":
    st.subheader("📖 Our Menu")

    col1, col2 = st.columns(2)

    with col1:
        st.markdown("""
        <div class="card">
            <h3>🍕 Main Course</h3>
            <p>Margherita Pizza – $10</p>
            <p>Grilled Chicken – $15</p>
            <p>Veggie Pasta – $12</p>
        </div>
        """, unsafe_allow_html=True)

    with col2:
        st.markdown("""
        <div class="card">
            <h3>🍰 Desserts</h3>
            <p>Chocolate Cake – $6</p>
            <p>Ice Cream – $5</p>
            <p>Cheesecake – $7</p>
        </div>
        """, unsafe_allow_html=True)

    st.markdown("""
    <div class="card">
        <h3>🥤 Drinks</h3>
        <p>Coffee – $3</p>
        <p>Fresh Juice – $4</p>
        <p>Soft Drinks – $2</p>
    </div>
    """, unsafe_allow_html=True)

# ---------- RESERVATIONS ----------
elif menu == "Reservations":
    st.subheader("📅 Book a Table")

    with st.form("reservation_form"):
        name = st.text_input("Name")
        date = st.date_input("Date")
        time = st.time_input("Time")
        people = st.number_input("Number of People", 1, 20)
        submit = st.form_submit_button("Reserve Table")

    if submit:
        st.success(
            f"✅ Reservation confirmed for **{name}** on **{date}** at **{time}** "
            f"for **{people} people**."
        )
        st.balloons()

# ---------- CONTACT ----------
elif menu == "Contact":
    st.subheader("📞 Contact Us")

    st.markdown("""
    <div class="card">
        <p>📍 Address: 123 Food Street, Flavor Town</p>
        <p>📞 Phone: +1 234 567 890</p>
        <p>📧 Email: contact@deliciousbites.com</p>
    </div>
    """, unsafe_allow_html=True)

    message = st.text_area("💬 Send us a message")
    if st.button("Send Message"):
        st.success("📨 Message sent successfully!")

# ---------- FOOTER ----------
st.markdown("---")
st.caption("© 2025 Delicious Bites Restaurant | Built with Streamlit 🍽️")
