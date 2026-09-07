<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MYBIRR - Digital Wallet</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
</head>
<body>
    <!-- App Container -->
    <div id="app">
        <!-- Splash Screen -->
        <div id="splash-screen" class="screen active">
            <div class="splash-content">
                <div class="splash-logo">
                    <i class="fas fa-wallet"></i>
                    <span>MYBIRR</span>
                </div>
                <div class="splash-loader">
                    <div class="loader"></div>
                </div>
                <p class="splash-text">Your Digital Wallet</p>
            </div>
        </div>

        <!-- Onboarding Screens -->
        <div id="onboarding-screen" class="screen">
            <div class="onboarding-container">
                <div class="onboarding-slides">
                    <div class="slide active" data-slide="0">
                        <div class="slide-icon">
                            <i class="fas fa-paper-plane"></i>
                        </div>
                        <h2>Send Money Instantly</h2>
                        <p>Send money to anyone in Ethiopia with just a few taps</p>
                    </div>
                    <div class="slide" data-slide="1">
                        <div class="slide-icon">
                            <i class="fas fa-store"></i>
                        </div>
                        <h2>Pay Anywhere</h2>
                        <p>Pay merchants, buy airtime, and settle bills easily</p>
                    </div>
                    <div class="slide" data-slide="2">
                        <div class="slide-icon">
                            <i class="fas fa-piggy-bank"></i>
                        </div>
                        <h2>Save & Grow</h2>
                        <p>Save money and access financial services</p>
                    </div>
                    <div class="slide" data-slide="3">
                        <div class="slide-icon">
                            <i class="fas fa-shield-alt"></i>
                        </div>
                        <h2>Secure & Trusted</h2>
                        <p>Your money is protected with advanced security</p>
                    </div>
                </div>
                <div class="onboarding-dots">
                    <span class="dot active" data-slide="0"></span>
                    <span class="dot" data-slide="1"></span>
                    <span class="dot" data-slide="2"></span>
                    <span class="dot" data-slide="3"></span>
                </div>
                <div class="onboarding-buttons">
                    <button class="btn-skip" onclick="skipOnboarding()">Skip</button>
                    <button class="btn-next" onclick="nextSlide()">Next</button>
                </div>
            </div>
        </div>

        <!-- Login Screen -->
        <div id="login-screen" class="screen">
            <div class="auth-container">
                <div class="auth-header">
                    <div class="auth-logo">
                        <i class="fas fa-wallet"></i>
                        <span>MYBIRR</span>
                    </div>
                    <h1>Welcome Back</h1>
                    <p>Sign in to your account</p>
                </div>
                <form id="login-form" onsubmit="handleLogin(event)">
                    <div class="form-group">
                        <label for="login-phone">Phone Number</label>
                        <div class="input-group">
                            <span class="input-prefix">+251</span>
                            <input type="tel" id="login-phone" placeholder="9XXXXXXXX" required>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="login-password">Password</label>
                        <div class="input-group">
                            <input type="password" id="login-password" placeholder="Enter your password" required>
                            <span class="input-icon toggle-password" onclick="togglePassword('login-password')">
                                <i class="fas fa-eye"></i>
                            </span>
                        </div>
                    </div>
                    <div class="form-options">
                        <label class="checkbox-label">
                            <input type="checkbox" checked> Remember me
                        </label>
                        <a href="#" onclick="showScreen('forgot-pin-screen')">Forgot PIN?</a>
                    </div>
                    <button type="submit" class="btn-primary btn-full">Sign In</button>
                </form>
                <div class="auth-footer">
                    <p>Don't have an account? <a href="#" onclick="showScreen('register-screen')">Create Account</a></p>
                </div>
            </div>
        </div>

        <!-- Register Screen -->
        <div id="register-screen" class="screen">
            <div class="auth-container">
                <div class="auth-header">
                    <div class="auth-logo">
                        <i class="fas fa-wallet"></i>
                        <span>MYBIRR</span>
                    </div>
                    <h1>Create Account</h1>
                    <p>Join the MYBIRR community</p>
                </div>
                <form id="register-form" onsubmit="handleRegister(event)">
                    <div class="form-group">
                        <label for="register-fullname">Full Name</label>
                        <input type="text" id="register-fullname" placeholder="Enter your full name" required>
                    </div>
                    <div class="form-group">
                        <label for="register-phone">Phone Number</label>
                        <div class="input-group">
                            <span class="input-prefix">+251</span>
                            <input type="tel" id="register-phone" placeholder="9XXXXXXXX" required>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="register-email">Email (Optional)</label>
                        <input type="email" id="register-email" placeholder="Enter your email">
                    </div>
                    <div class="form-group">
                        <label for="register-password">Password</label>
                        <div class="input-group">
                            <input type="password" id="register-password" placeholder="Create a password" required>
                            <span class="input-icon toggle-password" onclick="togglePassword('register-password')">
                                <i class="fas fa-eye"></i>
                            </span>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="register-pin">PIN (4 digits)</label>
                        <input type="password" id="register-pin" placeholder="Enter 4-digit PIN" maxlength="4" required>
                    </div>
                    <button type="submit" class="btn-primary btn-full">Create Account</button>
                </form>
                <div class="auth-footer">
                    <p>Already have an account? <a href="#" onclick="showScreen('login-screen')">Sign In</a></p>
                </div>
            </div>
        </div>

        <!-- OTP Verification Screen -->
        <div id="otp-screen" class="screen">
            <div class="auth-container">
                <div class="auth-header">
                    <div class="auth-logo">
                        <i class="fas fa-wallet"></i>
                        <span>MYBIRR</span>
                    </div>
                    <h1>Verify Your Phone</h1>
                    <p>We sent a 6-digit code to <span id="otp-phone">+251XXXXXXXXX</span></p>
                </div>
                <form id="otp-form" onsubmit="handleOTP(event)">
                    <div class="otp-inputs">
                        <input type="text" maxlength="1" class="otp-input" required>
                        <input type="text" maxlength="1" class="otp-input" required>
                        <input type="text" maxlength="1" class="otp-input" required>
                        <input type="text" maxlength="1" class="otp-input" required>
                        <input type="text" maxlength="1" class="otp-input" required>
                        <input type="text" maxlength="1" class="otp-input" required>
                    </div>
                    <button type="submit" class="btn-primary btn-full">Verify</button>
                </form>
                <div class="auth-footer">
                    <p>Didn't receive the code? <a href="#" onclick="resendOTP()">Resend</a></p>
                </div>
            </div>
        </div>

        <!-- Home/Dashboard Screen -->
        <div id="home-screen" class="screen">
            <!-- Header -->
            <div class="app-header">
                <div class="header-left">
                    <div class="app-logo">
                        <i class="fas fa-wallet"></i>
                        <span>MYBIRR</span>
                    </div>
                </div>
                <div class="header-right">
                    <button class="icon-btn" onclick="showScreen('notifications-screen')">
                        <i class="fas fa-bell"></i>
                        <span class="badge">3</span>
                    </button>
                    <div class="user-avatar" onclick="showScreen('profile-screen')">
                        <i class="fas fa-user"></i>
                    </div>
                </div>
            </div>

            <!-- Balance Card -->
            <div class="balance-card">
                <div class="balance-header">
                    <span class="balance-label">Available Balance</span>
                    <button class="icon-btn" onclick="toggleBalance()">
                        <i class="fas fa-eye" id="balance-toggle"></i>
                    </button>
                </div>
                <div class="balance-amount" id="wallet-balance">
                    <span class="currency">ETB</span>
                    <span class="amount">12,450.00</span>
                </div>
                <div class="balance-details">
                    <div class="balance-item">
                        <span class="label">Account Number</span>
                        <span class="value">MYB-2024-001</span>
                    </div>
                    <div class="balance-item">
                        <span class="label">KYC Level</span>
                        <span class="value badge-verified">Verified</span>
                    </div>
                </div>
            </div>

            <!-- Quick Actions -->
            <div class="quick-actions">
                <button class="action-btn" onclick="showScreen('send-screen')">
                    <div class="action-icon send">
                        <i class="fas fa-paper-plane"></i>
                    </div>
                    <span>Send</span>
                </button>
                <button class="action-btn" onclick="showScreen('receive-screen')">
                    <div class="action-icon receive">
                        <i class="fas fa-download"></i>
                    </div>
                    <span>Receive</span>
                </button>
                <button class="action-btn" onclick="showScreen('scan-screen')">
                    <div class="action-icon scan">
                        <i class="fas fa-qrcode"></i>
                    </div>
                    <span>Scan</span>
                </button>
                <button class="action-btn" onclick="showScreen('pay-screen')">
                    <div class="action-icon pay">
                        <i class="fas fa-store"></i>
                    </div>
                    <span>Pay</span>
                </button>
            </div>

            <!-- Services Grid -->
            <div class="services-grid">
                <button class="service-btn" onclick="showScreen('airtime-screen')">
                    <i class="fas fa-phone"></i>
                    <span>Airtime</span>
                </button>
                <button class="service-btn" onclick="showScreen('data-screen')">
                    <i class="fas fa-wifi"></i>
                    <span>Data</span>
                </button>
                <button class="service-btn" onclick="showScreen('bills-screen')">
                    <i class="fas fa-file-invoice"></i>
                    <span>Bills</span>
                </button>
                <button class="service-btn" onclick="showScreen('savings-screen')">
                    <i class="fas fa-piggy-bank"></i>
                    <span>Savings</span>
                </button>
            </div>

            <!-- Recent Transactions -->
            <div class="recent-transactions">
                <div class="section-header">
                    <h3>Recent Transactions</h3>
                    <a href="#" onclick="showScreen('transactions-screen')">View All</a>
                </div>
                <div class="transaction-list">
                    <div class="transaction-item">
                        <div class="tx-icon sent">
                            <i class="fas fa-arrow-up"></i>
                        </div>
                        <div class="tx-details">
                            <div class="tx-name">Sent to Abebe B.</div>
                            <div class="tx-date">Today, 14:30</div>
                        </div>
                        <div class="tx-amount negative">-ETB 500.00</div>
                    </div>
                    <div class="transaction-item">
                        <div class="tx-icon received">
                            <i class="fas fa-arrow-down"></i>
                        </div>
                        <div class="tx-details">
                            <div class="tx-name">Received from Alem M.</div>
                            <div class="tx-date">Today, 12:15</div>
                        </div>
                        <div class="tx-amount positive">+ETB 1,000.00</div>
                    </div>
                    <div class="transaction-item">
                        <div class="tx-icon payment">
                            <i class="fas fa-shopping-bag"></i>
                        </div>
                        <div class="tx-details">
                            <div class="tx-name">Payment to ABC Store</div>
                            <div class="tx-date">Yesterday, 18:45</div>
                        </div>
                        <div class="tx-amount negative">-ETB 250.00</div>
                    </div>
                    <div class="transaction-item">
                        <div class="tx-icon airtime">
                            <i class="fas fa-phone-alt"></i>
                        </div>
                        <div class="tx-details">
                            <div class="tx-name">Airtime Purchase</div>
                            <div class="tx-date">Yesterday, 10:20</div>
                        </div>
                        <div class="tx-amount negative">-ETB 50.00</div>
                    </div>
                </div>
            </div>

            <!-- Bottom Navigation -->
            <div class="bottom-nav">
                <button class="nav-item active" onclick="showScreen('home-screen')">
                    <i class="fas fa-home"></i>
                    <span>Home</span>
                </button>
                <button class="nav-item" onclick="showScreen('transactions-screen')">
                    <i class="fas fa-clock"></i>
                    <span>History</span>
                </button>
                <button class="nav-item" onclick="showScreen('scan-screen')">
                    <i class="fas fa-qrcode"></i>
                    <span>Scan</span>
                </button>
                <button class="nav-item" onclick="showScreen('profile-screen')">
                    <i class="fas fa-user"></i>
                    <span>Profile</span>
                </button>
            </div>
        </div>

        <!-- Send Money Screen -->
        <div id="send-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Send Money</h2>
            </div>
            <div class="send-container">
                <div class="form-group">
                    <label>Recipient</label>
                    <div class="recipient-select">
                        <input type="text" placeholder="Phone number or select contact" id="recipient-input">
                        <button class="icon-btn"><i class="fas fa-address-book"></i></button>
                    </div>
                </div>
                <div class="form-group">
                    <label>Amount (ETB)</label>
                    <div class="amount-input">
                        <span class="currency-prefix">ETB</span>
                        <input type="number" id="send-amount" placeholder="0.00" step="0.01">
                    </div>
                </div>
                <div class="form-group">
                    <label>Description (Optional)</label>
                    <input type="text" id="send-description" placeholder="What's this for?">
                </div>
                <div class="fee-info">
                    <div class="fee-row">
                        <span>Transfer Fee</span>
                        <span>ETB 5.00</span>
                    </div>
                    <div class="fee-row total">
                        <span>Total</span>
                        <span>ETB 505.00</span>
                    </div>
                </div>
                <button class="btn-primary btn-full" onclick="processSendMoney()">Send Money</button>
            </div>
        </div>

        <!-- Receive Money Screen -->
        <div id="receive-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Receive Money</h2>
            </div>
            <div class="receive-container">
                <div class="qr-container">
                    <div class="qr-code" id="qr-code">
                        <i class="fas fa-qrcode" style="font-size: 150px; color: #1a1a2e;"></i>
                    </div>
                    <div class="share-info">
                        <p class="qr-label">Scan to receive money</p>
                        <div class="qr-details">
                            <div class="detail-row">
                                <span>MYBIRR ID</span>
                                <span class="value">MYB-2024-001</span>
                            </div>
                            <div class="detail-row">
                                <span>Phone</span>
                                <span class="value">+251 912 345 678</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="share-actions">
                    <button class="btn-secondary" onclick="shareQR()">
                        <i class="fas fa-share-alt"></i> Share QR
                    </button>
                    <button class="btn-secondary" onclick="copyInfo()">
                        <i class="fas fa-copy"></i> Copy Details
                    </button>
                </div>
            </div>
        </div>

        <!-- Scan QR Screen -->
        <div id="scan-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Scan QR</h2>
            </div>
            <div class="scan-container">
                <div class="scanner-frame">
                    <div class="scanner-area">
                        <div class="scanner-corner tl"></div>
                        <div class="scanner-corner tr"></div>
                        <div class="scanner-corner bl"></div>
                        <div class="scanner-corner br"></div>
                        <div class="scanner-line"></div>
                        <i class="fas fa-camera scanner-icon"></i>
                    </div>
                    <p class="scan-instruction">Position QR code within the frame</p>
                </div>
                <div class="scan-options">
                    <button class="btn-secondary" onclick="uploadQR()">
                        <i class="fas fa-image"></i> Upload QR
                    </button>
                    <button class="btn-secondary" onclick="flashToggle()">
                        <i class="fas fa-bolt"></i> Flash
                    </button>
                </div>
            </div>
        </div>

        <!-- Airtime Screen -->
        <div id="airtime-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Buy Airtime</h2>
            </div>
            <div class="service-container">
                <div class="form-group">
                    <label>Phone Number</label>
                    <input type="tel" placeholder="Enter phone number" id="airtime-phone">
                </div>
                <div class="form-group">
                    <label>Amount (ETB)</label>
                    <div class="amount-presets">
                        <button class="preset-btn" onclick="setAirtimeAmount(10)">10</button>
                        <button class="preset-btn" onclick="setAirtimeAmount(25)">25</button>
                        <button class="preset-btn" onclick="setAirtimeAmount(50)">50</button>
                        <button class="preset-btn" onclick="setAirtimeAmount(100)">100</button>
                    </div>
                    <input type="number" id="airtime-amount" placeholder="Enter amount" step="1">
                </div>
                <div class="service-info">
                    <div class="info-row">
                        <span>Provider</span>
                        <span>Ethio Telecom</span>
                    </div>
                    <div class="info-row total">
                        <span>Total</span>
                        <span>ETB <span id="airtime-total">0.00</span></span>
                    </div>
                </div>
                <button class="btn-primary btn-full" onclick="processAirtime()">Buy Airtime</button>
            </div>
        </div>

        <!-- Bills Screen -->
        <div id="bills-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Pay Bills</h2>
            </div>
            <div class="service-container">
                <div class="bill-categories">
                    <button class="category-btn active" onclick="selectBillCategory('electricity')">
                        <i class="fas fa-bolt"></i>
                        <span>Electricity</span>
                    </button>
                    <button class="category-btn" onclick="selectBillCategory('water')">
                        <i class="fas fa-water"></i>
                        <span>Water</span>
                    </button>
                    <button class="category-btn" onclick="selectBillCategory('internet')">
                        <i class="fas fa-wifi"></i>
                        <span>Internet</span>
                    </button>
                    <button class="category-btn" onclick="selectBillCategory('tv')">
                        <i class="fas fa-tv"></i>
                        <span>TV</span>
                    </button>
                </div>
                <div class="form-group">
                    <label>Customer Number</label>
                    <input type="text" placeholder="Enter customer number" id="bill-customer">
                </div>
                <div class="form-group">
                    <label>Amount (ETB)</label>
                    <input type="number" placeholder="Enter amount" id="bill-amount">
                </div>
                <div class="service-info">
                    <div class="info-row">
                        <span>Service Fee</span>
                        <span>ETB 0.00</span>
                    </div>
                    <div class="info-row total">
                        <span>Total</span>
                        <span>ETB <span id="bill-total">0.00</span></span>
                    </div>
                </div>
                <button class="btn-primary btn-full" onclick="processBill()">Pay Bill</button>
            </div>
        </div>

        <!-- Transactions Screen -->
        <div id="transactions-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Transactions</h2>
            </div>
            <div class="transactions-container">
                <div class="filter-tabs">
                    <button class="filter-tab active" onclick="filterTransactions('all')">All</button>
                    <button class="filter-tab" onclick="filterTransactions('sent')">Sent</button>
                    <button class="filter-tab" onclick="filterTransactions('received')">Received</button>
                    <button class="filter-tab" onclick="filterTransactions('payments')">Payments</button>
                </div>
                <div class="transaction-list-full">
                    <!-- Transaction items would be dynamically loaded here -->
                    <div class="transaction-item">
                        <div class="tx-icon sent">
                            <i class="fas fa-arrow-up"></i>
                        </div>
                        <div class="tx-details">
                            <div class="tx-name">Sent to Abebe B.</div>
                            <div class="tx-date">Today, 14:30</div>
                            <div class="tx-reference">REF: MYB-2024-001</div>
                        </div>
                        <div class="tx-amount negative">-ETB 500.00</div>
                    </div>
                    <!-- More transactions... -->
                </div>
            </div>
        </div>

        <!-- Notifications Screen -->
        <div id="notifications-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Notifications</h2>
            </div>
            <div class="notifications-container">
                <div class="notification-item unread">
                    <div class="notif-icon">
                        <i class="fas fa-check-circle" style="color: #00c853;"></i>
                    </div>
                    <div class="notif-content">
                        <h4>Payment Received</h4>
                        <p>You received ETB 1,000.00 from Alem M.</p>
                        <span class="notif-time">2 minutes ago</span>
                    </div>
                </div>
                <div class="notification-item unread">
                    <div class="notif-icon">
                        <i class="fas fa-exclamation-circle" style="color: #ff9800;"></i>
                    </div>
                    <div class="notif-content">
                        <h4>Security Alert</h4>
                        <p>New login detected from Addis Ababa</p>
                        <span class="notif-time">1 hour ago</span>
                    </div>
                </div>
                <div class="notification-item">
                    <div class="notif-icon">
                        <i class="fas fa-gift" style="color: #e91e63;"></i>
                    </div>
                    <div class="notif-content">
                        <h4>Promotion</h4>
                        <p>Get 5% cashback on your next transfer</p>
                        <span class="notif-time">3 hours ago</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Profile Screen -->
        <div id="profile-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('home-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Profile</h2>
            </div>
            <div class="profile-container">
                <div class="profile-header">
                    <div class="profile-avatar">
                        <i class="fas fa-user" style="font-size: 60px;"></i>
                    </div>
                    <h3>Getachew T.</h3>
                    <p>+251 912 345 678</p>
                    <div class="profile-badge">Verified</div>
                </div>
                <div class="profile-menu">
                    <div class="menu-item" onclick="showScreen('kyc-screen')">
                        <i class="fas fa-id-card"></i>
                        <span>KYC Verification</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                    <div class="menu-item">
                        <i class="fas fa-shield-alt"></i>
                        <span>Security Settings</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                    <div class="menu-item">
                        <i class="fas fa-language"></i>
                        <span>Language</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                    <div class="menu-item">
                        <i class="fas fa-users"></i>
                        <span>Refer & Earn</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                    <div class="menu-item">
                        <i class="fas fa-question-circle"></i>
                        <span>Help & Support</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                    <div class="menu-item">
                        <i class="fas fa-info-circle"></i>
                        <span>About MYBIRR</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                    <div class="menu-item logout" onclick="handleLogout()">
                        <i class="fas fa-sign-out-alt"></i>
                        <span>Logout</span>
                        <i class="fas fa-chevron-right"></i>
                    </div>
                </div>
            </div>
        </div>

        <!-- Forgot PIN Screen -->
        <div id="forgot-pin-screen" class="screen">
            <div class="auth-container">
                <div class="auth-header">
                    <div class="auth-logo">
                        <i class="fas fa-wallet"></i>
                        <span>MYBIRR</span>
                    </div>
                    <h1>Reset PIN</h1>
                    <p>Enter your phone number to reset your PIN</p>
                </div>
                <form onsubmit="handleForgotPIN(event)">
                    <div class="form-group">
                        <label>Phone Number</label>
                        <div class="input-group">
                            <span class="input-prefix">+251</span>
                            <input type="tel" placeholder="9XXXXXXXX" required>
                        </div>
                    </div>
                    <button type="submit" class="btn-primary btn-full">Send Reset Code</button>
                </form>
                <div class="auth-footer">
                    <p><a href="#" onclick="showScreen('login-screen')">Back to Sign In</a></p>
                </div>
            </div>
        </div>

        <!-- KYC Screen -->
        <div id="kyc-screen" class="screen">
            <div class="screen-header">
                <button class="back-btn" onclick="showScreen('profile-screen')">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>KYC Verification</h2>
            </div>
            <div class="kyc-container">
                <div class="kyc-status">
                    <div class="status-badge verified">
                        <i class="fas fa-check-circle"></i>
                        Verified
                    </div>
                    <p>Your account is fully verified</p>
                </div>
                <div class="kyc-info">
                    <div class="info-item">
                        <span>Full Name</span>
                        <span>Getachew T.</span>
                    </div>
                    <div class="info-item">
                        <span>ID Type</span>
                        <span>National ID</span>
                    </div>
                    <div class="info-item">
                        <span>ID Number</span>
                        <span>1234567890</span>
                    </div>
                    <div class="info-item">
                        <span>Verification Date</span>
                        <span>15/01/2024</span>
                    </div>
                </div>
                <div class="kyc-levels">
                    <h4>Your Limits</h4>
                    <div class="limit-item">
                        <span>Daily Transfer</span>
                        <span>ETB 20,000</span>
                    </div>
                    <div class="limit-item">
                        <span>Monthly Transfer</span>
                        <span>ETB 100,000</span>
                    </div>
                    <div class="limit-item">
                        <span>Single Transaction</span>
                        <span>ETB 10,000</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modals -->
    <div id="modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modal-title">Success</h3>
                <button class="close-btn" onclick="closeModal()">&times;</button>
            </div>
            <div class="modal-body" id="modal-body">
                <p id="modal-message">Transaction completed successfully!</p>
            </div>
            <div class="modal-footer">
                <button class="btn-primary" onclick="closeModal()">OK</button>
            </div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>