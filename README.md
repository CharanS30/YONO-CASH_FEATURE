Web-Based YONO Cash Simulator  
A complete web-based simulation of SBI’s YONO Cash system including account creation, OTP login, cash withdrawal, cash deposit, and a virtual ATM machine for transaction execution.


Features

# User Authentication
- New user registration with:
  - Full details (name, dob, gender, address, email, etc.)
  - Email verification via OTP (valid for 5 minutes)
- Login with username + password
- Login OTP verification sent to registered email

# Account Creation
- Auto-generated:
  - 11-digit account number  
  - IFSC code  
- Default balance: ₹5000  
- Account details emailed to user after registration

# YONO Cash — Withdrawal
- User enters:
  - Withdrawal amount
  - 6-digit YONO PIN
- System generates a 6-digit reference number
- Reference sent via email (valid for 4 hours)
- Record stored in MongoDB
- Virtual ATM:
  - Enter reference number
  - Enter amount
  - Enter PIN
  - System validates and debits the amount
  - Sends transaction successful email
  - Updates account balance in database and UI


# YONO Cash — Deposit
- User selects "Deposit Cash"
- System generates reference number (no PIN required)
- Reference sent via email (valid for 4 hours)
- Virtual ATM:
  - Enter reference number
  - Validate
  - Enter deposit amount
  - Option to "Add More Cash"
  - Confirm to credit amount
  - System updates balance and emails user


# Virtual ATM Simulator
- Fully interactive ATM interface:
  - Numeric keypad
  - Reference number input
  - Amount entry
  - PIN entry (for withdrawal)
  - Processing animations
  - Success / failure screens
- Supports both:
  - Withdrawals  
  - Deposits  
- Auto-updates balance in MongoDB and UI


# Email Notifications (via Nodemailer + Gmail)
- Registration OTP  
- Login OTP  
- Account number + IFSC  
- YONO Cash reference number (withdraw / deposit)  
- Debit email on successful withdrawal  
- Credit email on successful deposit  


# Backend (Node.js + Express + MongoDB)
# Routes Included:
- `/api/auth` — Registration, Login, OTP
- `/api/account` — Account details, Balance check
- `/api/yono` — Generate YONO Reference numbers
- `/api/atm` — Validate reference, PIN, debit/credit balance  
- Static serving of frontend via Express

# Database Models:
- `User`
- `Otp`
- `YonoCash`


# Frontend
Built with **HTML, CSS, JavaScript**:
- Registration page
- Login page
- OTP verification page
- Home page (YONO Cash UI)
- Popup modal for Withdraw / Deposit flows
- Virtual ATM UI


Notes:
Gmail requires an “App Password” for Nodemailer (2FA must be enabled).
Reference numbers valid for 4 hours.
OTPs valid for 5 minutes.
PIN stored securely (hashed or original as per config).
