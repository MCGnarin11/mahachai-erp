<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mahachai Group - ระบบ ERP ครบวงจร</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --mahachai-orange: #FF8C42;
            --mahachai-brown: #8B4513;
            --primary-color: #2c3e50;
            --secondary-color: var(--mahachai-orange);
            --success-color: #27ae60;
            --warning-color: #f39c12;
            --danger-color: #e74c3c;
            --info-color: #16a085;
            --light-bg: #ecf0f1;
            --white: #ffffff;
            --text-dark: #2c3e50;
            --text-light: #7f8c8d;
            --border-color: #ddd;
            --shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        body {
            font-family: 'Sarabun', -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: var(--light-bg);
            color: var(--text-dark);
            line-height: 1.6;
        }
        
        /* Layout */
        .app-container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar */
        .sidebar {
            width: 280px;
            background: linear-gradient(135deg, var(--mahachai-brown) 0%, #5D4037 100%);
            color: white;
            padding: 0;
            box-shadow: 2px 0 10px rgba(0,0,0,0.15);
            position: fixed;
            height: 100vh;
            overflow-y: auto;
            transition: transform 0.3s ease;
        }
        
        .sidebar-header {
            padding: 20px;
            background: rgba(0,0,0,0.1);
            border-bottom: 1px solid rgba(255,255,255,0.1);
            text-align: center;
        }
        
        .logo-container {
            background: white;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        .logo-text {
            background: linear-gradient(45deg, var(--mahachai-orange), var(--mahachai-brown));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-size: 24px;
            font-weight: 700;
            text-align: center;
        }
        
        .company-slogan {
            font-size: 12px;
            color: rgba(255,255,255,0.8);
            text-align: center;
            margin-top: 5px;
        }
        
        .nav-menu {
            padding: 20px 0;
        }
        
        .nav-item {
            padding: 15px 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 12px;
            color: rgba(255,255,255,0.8);
            text-decoration: none;
            border-left: 3px solid transparent;
            margin: 2px 0;
        }
        
        .nav-item:hover {
            background: rgba(255,255,255,0.1);
            color: white;
            border-left-color: var(--mahachai-orange);
            transform: translateX(5px);
        }
        
        .nav-item.active {
            background: rgba(255,138,66,0.2);
            color: white;
            border-left-color: var(--mahachai-orange);
            box-shadow: inset 0 0 10px rgba(255,138,66,0.1);
        }
        
        .nav-icon {
            font-size: 20px;
            width: 24px;
            text-align: center;
        }
        
        /* Navigation Section Styles */
        .nav-section {
            margin: 10px 0;
        }
        
        .nav-section-header {
            padding: 15px 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 12px;
            color: rgba(255,255,255,0.6);
            border-left: 3px solid transparent;
            margin: 2px 0;
            background: rgba(0,0,0,0.1);
            position: relative;
        }
        
        .nav-section-header:hover {
            background: rgba(255,255,255,0.05);
            color: rgba(255,255,255,0.8);
            border-left-color: rgba(255,138,66,0.5);
        }
        
        .nav-arrow {
            margin-left: auto;
            transition: transform 0.3s ease;
            font-size: 12px;
        }
        
        .nav-section-header.active .nav-arrow {
            transform: rotate(180deg);
        }
        
        .nav-section-content {
            background: rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            overflow: hidden;
        }
        
        .nav-sub-item {
            padding: 12px 25px 12px 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 12px;
            color: rgba(255,255,255,0.6);
            text-decoration: none;
            border-left: 3px solid transparent;
            margin: 1px 0;
            font-size: 14px;
        }
        
        .nav-sub-item:hover {
            background: rgba(255,255,255,0.05);
            color: rgba(255,255,255,0.8);
            border-left-color: var(--mahachai-orange);
            transform: translateX(3px);
        }
        
        /* Radio button containers styling */
        label:has(input[name="paymentTerms"]),
        label:has(input[name="paymentStatus"]) {
            transition: all 0.3s ease !important;
            cursor: pointer !important;
        }
        
        label:has(input[name="paymentTerms"]:checked),
        label:has(input[name="paymentStatus"]:checked) {
            border-color: var(--mahachai-orange) !important;
            background-color: rgba(255, 138, 66, 0.1) !important;
        }
        
        label:has(input[name="paymentTerms"]):hover,
        label:has(input[name="paymentStatus"]):hover {
            border-color: var(--mahachai-orange) !important;
            background-color: rgba(255, 138, 66, 0.05) !important;
        }
        
        /* Main Content */
        .main-content {
            flex: 1;
            margin-left: 280px;
            padding: 20px;
            transition: margin-left 0.3s ease;
        }
        
        /* Header */
        .main-header {
            background: linear-gradient(135deg, white 0%, #f8f9fa 100%);
            padding: 25px 30px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            margin-bottom: 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-left: 5px solid var(--mahachai-orange);
        }
        
        .page-title {
            font-size: 28px;
            font-weight: 700;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .header-actions {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 10px 20px;
            background: linear-gradient(135deg, var(--mahachai-orange), #FF6B35);
            border-radius: 25px;
            color: white;
            box-shadow: 0 4px 12px rgba(255,138,66,0.3);
        }
        
        .user-avatar {
            width: 36px;
            height: 36px;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 600;
            font-size: 16px;
        }
        
        /* Dashboard Cards */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: white;
            padding: 30px 25px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            border-top: 4px solid var(--mahachai-orange);
        }
        
        .stat-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }
        
        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100px;
            height: 100px;
            background: linear-gradient(45deg, var(--mahachai-orange), transparent);
            opacity: 0.1;
            border-radius: 50%;
            transform: translate(30px, -30px);
        }
        
        .stat-card h3 {
            font-size: 14px;
            color: var(--text-light);
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
        }
        
        .stat-value {
            font-size: 36px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 12px;
            position: relative;
            z-index: 1;
        }
        
        .stat-change {
            font-size: 14px;
            color: var(--success-color);
            display: flex;
            align-items: center;
            gap: 5px;
            font-weight: 600;
        }
        
        .stat-change.negative {
            color: var(--danger-color);
        }
        
        /* Forms */
        .form-container {
            background: white;
            padding: 35px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            border-top: 4px solid var(--mahachai-orange);
        }
        
        .form-section {
            background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%);
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 1px solid #e9ecef;
            border-left: 4px solid var(--mahachai-orange);
        }
        
        .section-title {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary-color);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--text-dark);
            font-size: 14px;
        }
        
        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid var(--border-color);
            border-radius: 8px;
            font-size: 14px;
            transition: all 0.3s ease;
            background-color: white;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--mahachai-orange);
            box-shadow: 0 0 0 3px rgba(255,138,66,0.1);
        }
        
        /* Buttons */
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            text-decoration: none;
            position: relative;
            overflow: hidden;
        }
        
        .btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.3s ease, height 0.3s ease;
        }
        
        .btn:hover::before {
            width: 100%;
            height: 100%;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--mahachai-orange) 0%, #FF6B35 100%);
            color: white;
            box-shadow: 0 4px 12px rgba(255,138,66,0.3);
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255,138,66,0.4);
        }
        
        .btn-success {
            background: linear-gradient(135deg, var(--success-color) 0%, #229954 100%);
            color: white;
        }
        
        .btn-warning {
            background: linear-gradient(135deg, var(--warning-color) 0%, #F4D03F 100%);
            color: white;
        }
        
        .btn-danger {
            background: linear-gradient(135deg, var(--danger-color) 0%, #C0392B 100%);
            color: white;
        }
        
        .btn-secondary {
            background: linear-gradient(135deg, var(--text-light) 0%, #95A5A6 100%);
            color: white;
        }
        
        /* Tables */
        .table-container {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            border-top: 4px solid var(--mahachai-orange);
        }
        
        .table-header {
            padding: 25px 30px;
            background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%);
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .search-box {
            position: relative;
            max-width: 400px;
        }
        
        .search-box input {
            width: 100%;
            padding: 12px 45px 12px 15px;
            border: 2px solid var(--border-color);
            border-radius: 25px;
            font-size: 14px;
            transition: all 0.3s ease;
        }
        
        .search-box input:focus {
            border-color: var(--mahachai-orange);
            box-shadow: 0 0 0 3px rgba(255,138,66,0.1);
        }
        
        .search-box::after {
            content: '🔍';
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-light);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 18px 15px;
            text-align: left;
            font-weight: 700;
            color: var(--text-dark);
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            border-bottom: 2px solid var(--mahachai-orange);
        }
        
        td {
            padding: 18px 15px;
            border-bottom: 1px solid #f0f0f0;
            font-size: 14px;
        }
        
        tr:hover {
            background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%);
        }
        
        /* Badges */
        .badge {
            display: inline-block;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .badge-success {
            background: linear-gradient(135deg, rgba(39, 174, 96, 0.1) 0%, rgba(39, 174, 96, 0.2) 100%);
            color: var(--success-color);
            border: 1px solid var(--success-color);
        }
        
        .badge-warning {
            background: linear-gradient(135deg, rgba(243, 156, 18, 0.1) 0%, rgba(243, 156, 18, 0.2) 100%);
            color: var(--warning-color);
            border: 1px solid var(--warning-color);
        }
        
        .badge-danger {
            background: linear-gradient(135deg, rgba(231, 76, 60, 0.1) 0%, rgba(231, 76, 60, 0.2) 100%);
            color: var(--danger-color);
            border: 1px solid var(--danger-color);
        }
        
        .badge-info {
            background: linear-gradient(135deg, rgba(255, 138, 66, 0.1) 0%, rgba(255, 138, 66, 0.2) 100%);
            color: var(--mahachai-orange);
            border: 1px solid var(--mahachai-orange);
        }
        
        /* Quick Actions */
        .quick-actions {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .quick-action-btn {
            background: white;
            border: 2px solid var(--border-color);
            padding: 25px 20px;
            border-radius: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            color: var(--text-dark);
            position: relative;
            overflow: hidden;
        }
        
        .quick-action-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,138,66,0.1), transparent);
            transition: left 0.5s ease;
        }
        
        .quick-action-btn:hover::before {
            left: 100%;
        }
        
        .quick-action-btn:hover {
            border-color: var(--mahachai-orange);
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(255,138,66,0.2);
        }
        
        .quick-action-icon {
            font-size: 40px;
            margin-bottom: 15px;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.1));
        }
        
        .quick-action-title {
            font-weight: 600;
            font-size: 16px;
            color: var(--primary-color);
        }
        
        /* Enhanced Modals */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            z-index: 1000;
            animation: fadeIn 0.3s ease;
            backdrop-filter: blur(5px);
        }
        
        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background: white;
            border-radius: 15px;
            width: 90%;
            max-width: 700px;
            max-height: 90vh;
            overflow-y: auto;
            animation: slideInUp 0.3s ease;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        
        .modal-header {
            padding: 25px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%);
            border-radius: 15px 15px 0 0;
        }
        
        .modal-body {
            padding: 30px 25px;
        }
        
        .modal-footer {
            padding: 20px 25px;
            border-top: 1px solid var(--border-color);
            display: flex;
            justify-content: flex-end;
            gap: 15px;
            background: #f8f9fa;
            border-radius: 0 0 15px 15px;
        }
        
        /* Status indicators */
        .status-dot {
            display: inline-block;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            margin-right: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }
        
        .status-dot.active {
            background: var(--success-color);
            animation: pulse 2s infinite;
        }
        
        .status-dot.pending {
            background: var(--warning-color);
        }
        
        .status-dot.overdue {
            background: var(--danger-color);
            animation: blink 1s infinite;
        }
        
        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes slideInUp {
            from { transform: translateY(30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }
        
        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0.3; }
        }
        
        /* Enhanced Payment Details */
        .payment-details {
            background: linear-gradient(135deg, #e3f2fd 0%, #f0f8ff 100%);
            padding: 25px;
            border-radius: 12px;
            margin-top: 15px;
            border: 1px solid #2196F3;
            box-shadow: 0 4px 12px rgba(33, 150, 243, 0.1);
        }
        
        .cheque-warning {
            background: linear-gradient(135deg, #fff3cd 0%, #fef9e7 100%);
            border: 1px solid #ffc107;
            border-radius: 8px;
            padding: 15px;
            margin-top: 15px;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }
        
        /* Summary box */
        .summary-box {
            background: linear-gradient(135deg, #e8f5e9 0%, #f1f8e9 100%);
            padding: 25px;
            border-radius: 12px;
            margin-top: 20px;
            border: 2px solid #4caf50;
            box-shadow: 0 4px 12px rgba(76, 175, 80, 0.1);
        }
        
        /* Mobile Menu */
        .mobile-menu-toggle {
            display: none;
            position: fixed;
            top: 20px;
            left: 20px;
            z-index: 1001;
            background: var(--mahachai-orange);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 10px;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(255,138,66,0.3);
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .mobile-menu-toggle {
                display: block;
            }
            
            .sidebar {
                transform: translateX(-100%);
                z-index: 1000;
            }
            
            .sidebar.active {
                transform: translateX(0);
            }
            
            .main-content {
                margin-left: 0;
                padding: 15px;
            }
            
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .form-grid {
                grid-template-columns: 1fr;
            }
            
            .quick-actions {
                grid-template-columns: 1fr 1fr;
            }
            
            .table-container {
                overflow-x: auto;
            }
            
            .main-header {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
        }
        
        /* Loading animation */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid #f3f3f3;
            border-top: 3px solid var(--mahachai-orange);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Notification toast */
        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: white;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            border-left: 4px solid var(--success-color);
            z-index: 1001;
            transform: translateX(400px);
            transition: transform 0.3s ease;
        }
        
        .toast.show {
            transform: translateX(0);
        }
        
        .toast.error {
            border-left-color: var(--danger-color);
        }
        
        .toast.warning {
            border-left-color: var(--warning-color);
        }
    </style>
</head>
<body>
    <button class="mobile-menu-toggle" onclick="toggleSidebar()">☰</button>
    
    <div class="app-container">
        <!-- Sidebar -->
        <aside class="sidebar" id="sidebar">
            <div class="sidebar-header">
                <div class="logo-container">
                    <div>
                        <div class="logo-text">Mahachai<br>Group</div>
                    </div>
    
    <!-- Add/Edit Supplier Modal -->
    <div id="addSupplierModal" class="modal">
        <div class="modal-content" style="max-width: 900px;">
            <div class="modal-header">
                <h2 id="supplierModalTitle">เพิ่มข้อมูล Supplier</h2>
                <button onclick="closeModal('addSupplierModal')" style="background: none; border: none; font-size: 24px; cursor: pointer;">×</button>
            </div>
            <div class="modal-body">
                <form id="supplierForm">
                    <!-- Basic Information -->
                    <div class="form-section">
                        <h4 class="section-title">
                            <span>📝</span> ข้อมูลพื้นฐาน
                        </h4>
                        <div class="form-grid">
                            <div class="form-group">
                                <label>รหัส Supplier</label>
                                <input type="text" class="form-control" id="supplierCode" value="00005" readonly style="background: #f0f0f0; font-weight: 600;">
                                <small style="color: #666;">รหัสจะถูกสร้างอัตโนมัติ</small>
                            </div>
                            <div class="form-group">
                                <label>ชื่อเรียก <span style="color: red;">*</span></label>
                                <input type="text" class="form-control" id="supplierNickname" placeholder="เช่น ทวีวงษ์" required>
                                <small style="color: #666;">ชื่อย่อสำหรับเรียกง่าย</small>
                            </div>
                            <div class="form-group" style="grid-column: 1 / -1;">
                                <label>ชื่อ Supplier เต็ม <span style="color: red;">*</span></label>
                                <input type="text" class="form-control" id="supplierFullName" placeholder="เช่น บริษัท ทวีวงษ์อุตสาหกรรม จำกัด" required>
                            </div>
                            <div class="form-group">
                                <label>จ่ายในนาม <span style="color: red;">*</span></label>
                                <select class="form-control" id="paymentEntity" required>
                                    <option value="">-- เลือกรายการ --</option>
                                    <option value="company">บริษัท</option>
                                    <option value="wipaporn">วิภาภรณ์</option>
                                </select>
                                <small style="color: #666;">เลือกว่าจะจ่ายในนามใคร</small>
                            </div>
                            <div class="form-group">
                                <label>Tax ID</label>
                                <input type="text" class="form-control" id="supplierTaxId" placeholder="0-0000-00000-00-0" maxlength="17">
                                <small style="color: #666;">ใส่เฉพาะบริษัทที่มี Tax ID</small>
                            </div>
                        </div>
                    </div>

                    <!-- Contact Information -->
                    <div class="form-section">
                        <h4 class="section-title">
                            <span>📞</span> ข้อมูลติดต่อ
                        </h4>
                        <div class="form-group">
                            <label>ที่อยู่ <span style="color: red;">*</span></label>
                            <textarea class="form-control" id="supplierAddress" rows="3" placeholder="ระบุที่อยู่ของ Supplier" required></textarea>
                        </div>
                        <div class="form-group">
                            <label>เบอร์ติดต่อ <span style="color: red;">*</span></label>
                            <input type="tel" class="form-control" id="supplierPhone" placeholder="0-0000-0000 หรือ 081-234-5678" required>
                        </div>
                    </div>

                    <!-- Payment Terms -->
                    <div class="form-section">
                        <h4 class="section-title">
                            <span>💰</span> ลักษณะการรับเงิน
                        </h4>
                        <div class="form-group">
                            <label>ลักษณะการรับเงิน <span style="color: red;">*</span></label>
                            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-top: 10px;">
                                <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 12px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;">
                                    <input type="radio" name="paymentTerms" value="due_date" onchange="toggleDueDateInput()"> 
                                    <span>เรียกเก็บตาม Due date</span>
                                </label>
                                <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 12px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;">
                                    <input type="radio" name="paymentTerms" value="monday" onchange="toggleDueDateInput()"> 
                                    <span>ชำระเงินทุกวันจันทร์</span>
                                </label>
                                <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 12px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;">
                                    <input type="radio" name="paymentTerms" value="cash_cheque" onchange="toggleDueDateInput()"> 
                                    <span>เงินสด/เช็ค</span>
                                </label>
                                <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 12px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;">
                                    <input type="radio" name="paymentTerms" value="next_bill" onchange="toggleDueDateInput()"> 
                                    <span>เรียกทุกบิลถัดไป</span>
                                </label>
                            </div>
                            <div id="dueDateInput" style="display: none; margin-top: 15px;">
                                <label>จำนวนวัน <span style="color: red;">*</span></label>
                                <div style="display: flex; align-items: center; gap: 10px;">
                                    <input type="number" class="form-control" id="dueDays" min="1" max="365" placeholder="30" style="width: 120px;">
                                    <span>วัน</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Bank Accounts -->
                    <div class="form-section">
                        <h4 class="section-title">
                            <span>🏦</span> ข้อมูลบัญชีธนาคาร
                            <small style="color: #666; font-weight: normal; margin-left: 10px;">(สูงสุด 5 บัญชี)</small>
                        </h4>
                        <div id="bankAccountsList">
                            <!-- Bank accounts will be populated here -->
                        </div>
                        <button type="button" class="btn btn-secondary" onclick="addBankAccount()" id="addBankBtn">
                            <span>➕</span> เพิ่มบัญชีธนาคาร
                        </button>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" onclick="closeModal('addSupplierModal')">ยกเลิก</button>
                <button class="btn btn-primary" onclick="saveSupplier()">
                    <span>💾</span> บันทึก
                </button>
            </div>
        </div>
    </div>
    
    <!-- Bank Accounts Modal -->
    <div id="bankAccountsModal" class="modal">
        <div class="modal-content" style="max-width: 800px;">
            <div class="modal-header">
                <h2>บัญชีธนาคารของ <span id="supplierNameInModal">-</span></h2>
                <button onclick="closeModal('bankAccountsModal')" style="background: none; border: none; font-size: 24px; cursor: pointer;">×</button>
            </div>
            <div class="modal-body">
                <div id="bankAccountsListView" style="max-height: 400px; overflow-y: auto;">
                    <!-- Bank accounts will be loaded here -->
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" onclick="closeModal('bankAccountsModal')">ปิด</button>
            </div>
        </div>
    </div>
                </div>
                <div class="company-slogan">สินค้าคุณภาพ สะอาด ราคาประหยัด</div>
            </div>
            <nav class="nav-menu">
                <a href="#" class="nav-item active" onclick="showPage('dashboard', this); return false;">
                    <span class="nav-icon">🏠</span>
                    <span>หน้าหลัก</span>
                </a>
                <a href="#" class="nav-item" onclick="showPage('purchase', this); return false;">
                    <span class="nav-icon">📄</span>
                    <span>บันทึกเอกสารซื้อ</span>
                </a>
                <a href="#" class="nav-item" onclick="showPage('supplier', this); return false;">
                    <span class="nav-icon">👥</span>
                    <span>จัดการ Supplier</span>
                </a>
                <a href="#" class="nav-item" onclick="showPage('sales-summary', this); return false;">
                    <span class="nav-icon">💰</span>
                    <span>บันทึกยอดขาย</span>
                </a>
                <a href="#" class="nav-item" onclick="showPage('cheque', this); return false;">
                    <span class="nav-icon">💳</span>
                    <span>จัดการเช็ค</span>
                </a>
                <a href="#" class="nav-item" onclick="showPage('reports', this); return false;">
                    <span class="nav-icon">📊</span>
                    <span>รายงาน</span>
                </a>
                <a href="#" class="nav-item" onclick="showPage('settings', this); return false;">
                    <span class="nav-icon">⚙️</span>
                    <span>ตั้งค่า</span>
                </a>
                
                <!-- Development Section -->
                <div class="nav-section">
                    <div class="nav-section-header" onclick="toggleNavSection('development')">
                        <span class="nav-icon">🚧</span>
                        <span>รอการพัฒนา</span>
                        <span class="nav-arrow">▼</span>
                    </div>
                    <div class="nav-section-content" id="development-section" style="display: none;">
                        <a href="#" class="nav-sub-item" onclick="showPage('inventory', this); return false;">
                            <span class="nav-icon">📦</span>
                            <span>จัดการสินค้า</span>
                        </a>
                        <a href="#" class="nav-sub-item" onclick="showPage('sales', this); return false;">
                            <span class="nav-icon">🛒</span>
                            <span>บันทึกเอกสารขาย</span>
                        </a>
                        <a href="#" class="nav-sub-item" onclick="showPage('customer', this); return false;">
                            <span class="nav-icon">👤</span>
                            <span>จัดการลูกค้า</span>
                        </a>
                    </div>
                </div>
            </nav>
        </aside>
        
        <!-- Main Content -->
        <main class="main-content">
            <!-- Dashboard Page -->
            <div id="dashboard-page" class="page-content">
                <div class="main-header">
                    <h1 class="page-title">
                        <span>📊</span>
                        Dashboard - Mahachai Group
                    </h1>
                    <div class="header-actions">
                        <div class="user-info">
                            <div class="user-avatar">M</div>
                            <span>Mahachai Admin</span>
                        </div>
                    </div>
                </div>
                
                <div class="dashboard-grid">
                    <div class="stat-card">
                        <h3>ยอดซื้อเดือนนี้</h3>
                        <div class="stat-value">฿ 850,000</div>
                        <div class="stat-change">
                            <span>↑ 15%</span> จากเดือนที่แล้ว
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <h3>ยอดขายเดือนนี้</h3>
                        <div class="stat-value">฿ 1,250,000</div>
                        <div class="stat-change">
                            <span>↑ 8%</span> จากเดือนที่แล้ว
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <h3>เจ้าหนี้คงค้าง</h3>
                        <div class="stat-value">฿ 185,000</div>
                        <div class="stat-change negative">
                            <span>↑ 5%</span> จากเดือนที่แล้ว
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <h3>ลูกหนี้คงค้าง</h3>
                        <div class="stat-value">฿ 320,000</div>
                        <div class="stat-change">
                            <span>↓ 3%</span> จากเดือนที่แล้ว
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <h3>สินค้าคงคลัง</h3>
                        <div class="stat-value">2,145 รายการ</div>
                        <div class="stat-change">
                            <span>฿ 1,850,000</span> มูลค่า
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <h3>เช็ครอเคลียร์</h3>
                        <div class="stat-value">18 ใบ</div>
                        <div class="stat-change">
                            <span>฿ 285,000</span> รวม
                        </div>
                    </div>
                </div>
                
                <h2 style="margin: 30px 0 20px; color: var(--primary-color); font-weight: 700;">🚀 Quick Actions</h2>
                <div class="quick-actions">
                    <a href="#" class="quick-action-btn" onclick="showPage('purchase', document.querySelector('.nav-item:nth-child(2)')); return false;">
                        <div class="quick-action-icon">➕</div>
                        <div class="quick-action-title">เอกสารซื้อใหม่</div>
                    </a>
                    <a href="#" class="quick-action-btn" onclick="showPage('supplier', document.querySelector('.nav-item:nth-child(3)')); return false;">
                        <div class="quick-action-icon">👥</div>
                        <div class="quick-action-title">จัดการ Supplier</div>
                    </a>
                    <a href="#" class="quick-action-btn" onclick="showPage('sales-summary', document.querySelector('.nav-item:nth-child(4)')); return false;">
                        <div class="quick-action-icon">💰</div>
                        <div class="quick-action-title">บันทึกยอดขาย</div>
                    </a>
                    <a href="#" class="quick-action-btn" onclick="showPage('cheque', document.querySelector('.nav-item:nth-child(5)')); return false;">
                        <div class="quick-action-icon">✅</div>
                        <div class="quick-action-title">อัปเดตเช็ค</div>
                    </a>
                </div>
                
                <!-- Recent Transactions -->
                <div class="table-container">
                    <div class="table-header">
                        <h3 style="color: var(--primary-color); font-weight: 700;">📋 รายการล่าสุด</h3>
                        <a href="#" class="btn btn-primary btn-sm">ดูทั้งหมด</a>
                    </div>
                    <table>
                        <thead>
                            <tr>
                                <th>วันที่</th>
                                <th>ประเภท</th>
                                <th>เลขที่เอกสาร</th>
                                <th>คู่ค้า</th>
                                <th>ยอดเงิน</th>
                                <th>สถานะ</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>09/01/2025</td>
                                <td><span class="badge badge-info">ขาย</span></td>
                                <td>SO2025-008</td>
                                <td>บริษัท ABC จำกัด</td>
                                <td style="color: var(--success-color); font-weight: 600;">+฿ 45,000</td>
                                <td><span class="status-dot active"></span>ชำระแล้ว</td>
                            </tr>
                            <tr>
                                <td>08/01/2025</td>
                                <td><span class="badge badge-warning">ซื้อ</span></td>
                                <td>PO2025-001</td>
                                <td>ทวีวงษ์</td>
                                <td style="color: var(--danger-color); font-weight: 600;">-฿ 15,500</td>
                                <td><span class="status-dot pending"></span>รอเคลียร์</td>
                            </tr>
                            <tr>
                                <td>07/01/2025</td>
                                <td><span class="badge badge-info">ขาย</span></td>
                                <td>SO2025-007</td>
                                <td>ร้านสมใจ</td>
                                <td style="color: var(--success-color); font-weight: 600;">+฿ 28,200</td>
                                <td><span class="status-dot active"></span>ชำระแล้ว</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Inventory Management Page -->
            <div id="inventory-page" class="page-content" style="display: none;">
                <div class="main-header">
                    <h1 class="page-title">
                        <span>📦</span>
                        จัดการสินค้าคงคลัง
                    </h1>
                    <div class="header-actions">
                        <button class="btn btn-primary" onclick="showAddProduct()">
                            <span>➕</span> เพิ่มสินค้า
                        </button>
                    </div>
                </div>
                
                <div class="dashboard-grid" style="margin-bottom: 30px;">
                    <div class="stat-card">
                        <h3>สินค้าทั้งหมด</h3>
                        <div class="stat-value">2,145</div>
                        <div class="stat-change">รายการ</div>
                    </div>
                    <div class="stat-card">
                        <h3>มูลค่าสินค้าคงคลัง</h3>
                        <div class="stat-value">฿ 1,850,000</div>
                        <div class="stat-change">ณ วันที่ 09/01/2025</div>
                    </div>
                    <div class="stat-card">
                        <h3>สินค้าใกล้หมด</h3>
                        <div class="stat-value">23</div>
                        <div class="stat-change negative">รายการ</div>
                    </div>
                    <div class="stat-card">
                        <h3>สินค้าขายดี</h3>
                        <div class="stat-value">156</div>
                        <div class="stat-change">รายการ (เดือนนี้)</div>
                    </div>
                </div>
                
                <div class="table-container">
                    <div class="table-header">
                        <div class="search-box">
                            <input type="text" placeholder="ค้นหาสินค้า รหัสสินค้า หรือบาร์โค้ด...">
                        </div>
                        <div style="display: flex; gap: 10px;">
                            <select class="form-control" style="width: 200px;">
                                <option>หมวดหมู่ทั้งหมด</option>
                                <option>อาหารแห้ง</option>
                                <option>เครื่องดื่ม</option>
                                <option>ของใช้ในครัว</option>
                                <option>เครื่องปรุงรส</option>
                            </select>
                            <button class="btn btn-success btn-sm">
                                <span>📊</span> Export
                            </button>
                        </div>
                    </div>
                    <table>
                        <thead>
                            <tr>
                                <th>รูปสินค้า</th>
                                <th>รหัสสินค้า</th>
                                <th>ชื่อสินค้า</th>
                                <th>หมวดหมู่</th>
                                <th>หน่วยนับ</th>
                                <th>ราคาซื้อ</th>
                                <th>ราคาขาย</th>
                                <th>คงเหลือ</th>
                                <th>สถานะ</th>
                                <th>การดำเนินการ</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>
                                    <div style="width: 50px; height: 50px; background: #f0f0f0; border-radius: 8px; display: flex; align-items: center; justify-content: center;">
                                        🍚
                                    </div>
                                </td>
                                <td>P001</td>
                                <td>ข้าวหอมมะลิ 5 กก.</td>
                                <td><span class="badge badge-info">อาหารแห้ง</span></td>
                                <td>ถุง</td>
                                <td style="text-align: right;">฿ 180</td>
                                <td style="text-align: right;">฿ 220</td>
                                <td style="text-align: center; font-weight: 600;">145</td>
                                <td><span class="badge badge-success">ปกติ</span></td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editProduct('P001')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="adjustStock('P001')">📊</button>
                                </td>
                            </tr>
                            <tr>
                                <td>
                                    <div style="width: 50px; height: 50px; background: #f0f0f0; border-radius: 8px; display: flex; align-items: center; justify-content: center;">
                                        🍯
                                    </div>
                                </td>
                                <td>P002</td>
                                <td>น้ำมันปาล์ม 1 ลิตร</td>
                                <td><span class="badge badge-info">อาหารแห้ง</span></td>
                                <td>ขวด</td>
                                <td style="text-align: right;">฿ 45</td>
                                <td style="text-align: right;">฿ 65</td>
                                <td style="text-align: center; font-weight: 600; color: var(--danger-color);">8</td>
                                <td><span class="badge badge-danger">ใกล้หมด</span></td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editProduct('P002')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="adjustStock('P002')">📊</button>
                                </td>
                            </tr>
                            <tr>
                                <td>
                                    <div style="width: 50px; height: 50px; background: #f0f0f0; border-radius: 8px; display: flex; align-items: center; justify-content: center;">
                                        🥤
                                    </div>
                                </td>
                                <td>P003</td>
                                <td>น้ำดื่ม 600 มล.</td>
                                <td><span class="badge badge-warning">เครื่องดื่ม</span></td>
                                <td>ขวด</td>
                                <td style="text-align: right;">฿ 5</td>
                                <td style="text-align: right;">฿ 8</td>
                                <td style="text-align: center; font-weight: 600;">380</td>
                                <td><span class="badge badge-success">ปกติ</span></td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editProduct('P003')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="adjustStock('P003')">📊</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Purchase Document Page -->
            <div id="purchase-page" class="page-content" style="display: none;">
                <div class="main-header">
                    <h1 class="page-title">
                        <span>📄</span>
                        บันทึกเอกสารซื้อ
                    </h1>
                </div>
                
                <div class="form-container">
                    <form id="purchaseForm">
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>📝</span> ข้อมูลเอกสาร
                            </h3>
                            <div class="form-grid">
                                <div class="form-group">
                                    <label>วันที่เอกสาร <span style="color: red;">*</span></label>
                                    <input type="date" class="form-control" id="docDate" required>
                                </div>
                                <div class="form-group">
                                    <label>เลขที่เอกสาร <span style="color: red;">*</span></label>
                                    <input type="text" class="form-control" placeholder="PO2025-001" required>
                                </div>
                                <div class="form-group">
                                    <label>วันที่บันทึกเอกสาร</label>
                                    <input type="date" class="form-control" id="recordDate" readonly style="background-color: #f0f0f0; cursor: not-allowed;">
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>👥</span> ข้อมูล Supplier
                            </h3>
                            <div class="form-group">
                                <label>ชื่อผู้ขาย (Supplier) <span style="color: red;">*</span></label>
                                <select class="form-control" onchange="updateSupplierInfo()" required>
                                    <option value="">-- เลือกผู้ขาย --</option>
                                    <option value="1" data-payee="บริษัท" data-payment="เครดิต 30 วัน">[00001] ทวีวงษ์ - บริษัท ทวีวงษ์อุตสาหกรรม จำกัด</option>
                                    <option value="2" data-payee="วิภาภรณ์" data-payment="เงินสด/เช็ค">[00002] สมชาย - คุณสมชาย ใจดี</option>
                                </select>
                            </div>
                            <div id="supplierInfo" style="display: none; background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%); padding: 20px; border-radius: 12px; margin-top: 15px; border: 1px solid #e9ecef;">
                                <p style="margin: 0; color: #666; font-size: 14px;">
                                    <strong>จ่ายในนาม:</strong> <span id="payeeInfo">-</span> | 
                                    <strong>เงื่อนไขการชำระ:</strong> <span id="paymentInfo">-</span>
                                </p>
                            </div>
                        </div>
                        
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>💰</span> การชำระเงิน
                            </h3>
                            
                            <!-- Payment Status Selection -->
                            <div class="form-group">
                                <label>สถานะการชำระเงิน <span style="color: red;">*</span></label>
                                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; margin-top: 10px;">
                                    <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 15px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;" onclick="selectPaymentStatus(this, 'paid')">
                                        <input type="radio" name="paymentStatus" value="paid" onchange="togglePaymentStatusDetails()"> 
                                        <div>
                                            <div style="font-weight: 600; color: var(--success-color);">จ่ายชำระแล้ว</div>
                                            <small style="color: #666;">ชำระเงินเรียบร้อยแล้ว</small>
                                        </div>
                                    </label>
                                    <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 15px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;" onclick="selectPaymentStatus(this, 'pending_bill')">
                                        <input type="radio" name="paymentStatus" value="pending_bill" onchange="togglePaymentStatusDetails()"> 
                                        <div>
                                            <div style="font-weight: 600; color: var(--warning-color);">รอเอกสารวางบิล</div>
                                            <small style="color: #666;">รอใบแจ้งหนี้จาก Supplier</small>
                                        </div>
                                    </label>
                                    <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px; padding: 15px; border: 2px solid #e9ecef; border-radius: 8px; transition: all 0.3s ease;" onclick="selectPaymentStatus(this, 'weekly_transfer')">
                                        <input type="radio" name="paymentStatus" value="weekly_transfer" onchange="togglePaymentStatusDetails()"> 
                                        <div>
                                            <div style="font-weight: 600; color: var(--info-color);">รอโอนชำระประจำสัปดาห์</div>
                                            <small style="color: #666;">รอโอนเงินตามกำหนด</small>
                                        </div>
                                    </label>
                                </div>
                            </div>
                            
                            <!-- Payment Method Section (Show only when "จ่ายชำระแล้ว" is selected) -->
                            <div id="paymentMethodSection" style="display: none;">
                                <div class="form-group" style="margin-top: 25px;">
                                    <label>ลักษณะการชำระเงิน <span style="color: red;">*</span></label>
                                    <div style="display: flex; gap: 20px; margin-top: 10px; flex-wrap: wrap;">
                                        <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px;">
                                            <input type="radio" name="paymentMethod" value="cash" onchange="togglePaymentDetails()"> เงินสด
                                        </label>
                                        <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px;">
                                            <input type="radio" name="paymentMethod" value="cheque" onchange="togglePaymentDetails()"> เช็ค
                                        </label>
                                        <label style="font-weight: normal; cursor: pointer; display: flex; align-items: center; gap: 8px;">
                                            <input type="radio" name="paymentMethod" value="transfer" onchange="togglePaymentDetails()"> เงินโอน
                                        </label>
                                    </div>
                                </div>
                                
                                <!-- Transfer Details -->
                                <div id="transferDetails" class="payment-details" style="display: none; background: linear-gradient(135deg, #e8f5e9 0%, #f1f8e9 100%); border-color: #4caf50;">
                                    <h4 style="margin-bottom: 20px; color: var(--primary-color); display: flex; align-items: center; gap: 10px;">
                                        <span>🏦</span> ข้อมูลการโอนเงิน
                                    </h4>
                                    <div class="form-grid">
                                        <div class="form-group">
                                            <label>บัญชีธนาคารของ Supplier <span style="color: red;">*</span></label>
                                            <select class="form-control" id="supplierBankAccount" onchange="updateBankAccountInfo()">
                                                <option value="">-- เลือกบัญชีธนาคาร --</option>
                                                <!-- Will be populated based on selected supplier -->
                                            </select>
                                        </div>
                                        <div class="form-group">
                                            <label>วันที่โอน</label>
                                            <input type="date" class="form-control">
                                        </div>
                                    </div>
                                    <div id="bankAccountInfo" style="display: none; background: rgba(255,255,255,0.8); padding: 15px; border-radius: 8px; margin-top: 15px; border: 1px solid #c8e6c9;">
                                        <h5 style="margin-bottom: 10px; color: var(--primary-color);">ข้อมูลบัญชีที่เลือก</h5>
                                        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 10px; font-size: 14px;">
                                            <p style="margin: 0;"><strong>ธนาคาร:</strong> <span id="bankName">-</span></p>
                                            <p style="margin: 0;"><strong>เลขที่บัญชี:</strong> <span id="accountNumber">-</span></p>
                                            <p style="margin: 0;"><strong>ชื่อบัญชี:</strong> <span id="accountName">-</span></p>
                                        </div>
                                    </div>
                                </div>
                                
                                <!-- Cheque Details -->
                                <div id="chequeDetails" class="payment-details" style="display: none;">
                                    <h4 style="margin-bottom: 20px; color: var(--primary-color); display: flex; align-items: center; gap: 10px;">
                                        <span>💳</span> ข้อมูลเช็ค
                                    </h4>
                                    <div class="form-grid">
                                        <div class="form-group">
                                            <label>วันที่เช็ค</label>
                                            <input type="date" class="form-control">
                                        </div>
                                        <div class="form-group">
                                            <label>เลขที่เช็ค</label>
                                            <input type="text" class="form-control" placeholder="เลขที่เช็ค">
                                        </div>
                                        <div class="form-group">
                                            <label>ธนาคาร</label>
                                            <select class="form-control">
                                                <option value="">-- เลือกธนาคาร --</option>
                                                <option value="BBL">ธนาคารกรุงเทพ</option>
                                                <option value="KBANK">ธนาคารกสิกรไทย</option>
                                                <option value="SCB">ธนาคารไทยพาณิชย์</option>
                                                <option value="KTB">ธนาคารกรุงไทย</option>
                                            </select>
                                        </div>
                                        <div class="form-group">
                                            <label>ยอดเงินเช็ค</label>
                                            <input type="number" class="form-control" step="0.01" placeholder="0.00">
                                        </div>
                                    </div>
                                    <div class="cheque-warning">
                                        <span style="color: #ffc107; font-size: 20px;">⚠️</span>
                                        <div style="flex: 1; color: #856404; font-size: 14px;">
                                            <strong>หมายเหตุ:</strong> ยอดเงินที่หน้าเช็คควรตรงกับยอดรวมที่ต้องชำระ
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Due Date Info (Show when "รอเอกสารวางบิล" or "รอโอนชำระประจำสัปดาห์" is selected) -->
                            <div id="dueDateInfo" style="display: none; margin-top: 20px;">
                                <div class="payment-details" style="background: linear-gradient(135deg, #fff3cd 0%, #fef9e7 100%); border-color: #ffc107;">
                                    <h4 style="margin-bottom: 20px; color: var(--primary-color); display: flex; align-items: center; gap: 10px;">
                                        <span>📅</span> ข้อมูลกำหนดชำระ
                                    </h4>
                                    <div class="form-grid">
                                        <div class="form-group">
                                            <label>วันครบกำหนดชำระ (คาดการณ์)</label>
                                            <input type="date" class="form-control" id="expectedDueDate" readonly style="background: #f8f9fa;">
                                        </div>
                                        <div class="form-group">
                                            <label>หมายเหตุ</label>
                                            <input type="text" class="form-control" placeholder="เช่น รอใบแจ้งหนี้, รอโอนวันจันทร์">
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>🧮</span> รายละเอียดยอดเงิน
                            </h3>
                            <div class="form-grid">
                                <div class="form-group">
                                    <label>ยอดเงินก่อน VAT <span style="color: red;">*</span></label>
                                    <input type="number" class="form-control" step="0.01" placeholder="0.00" onchange="calculateVAT()" id="beforeVat">
                                </div>
                                <div class="form-group">
                                    <label>ประเภท VAT <span style="color: red;">*</span></label>
                                    <div style="display: flex; gap: 20px; margin-top: 10px;">
                                        <label style="font-weight: normal; display: flex; align-items: center; gap: 8px;">
                                            <input type="radio" name="vatType" value="vat" onchange="calculateVAT()"> มี VAT (7%)
                                        </label>
                                        <label style="font-weight: normal; display: flex; align-items: center; gap: 8px;">
                                            <input type="radio" name="vatType" value="non_vat" onchange="calculateVAT()"> ไม่มี VAT
                                        </label>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="summary-box">
                                <h4 style="margin-bottom: 20px; color: var(--primary-color); display: flex; align-items: center; gap: 10px;">
                                    <span>💵</span> สรุปยอดเงิน
                                </h4>
                                <div style="display: flex; justify-content: space-between; margin-bottom: 15px; padding: 10px 0; border-bottom: 1px solid #e9ecef;">
                                    <span style="font-weight: 600;">ยอดเงินก่อน VAT:</span>
                                    <span id="subtotal" style="font-weight: 700; color: var(--primary-color);">0.00</span>
                                </div>
                                <div style="display: flex; justify-content: space-between; margin-bottom: 15px; padding: 10px 0; border-bottom: 1px solid #e9ecef;">
                                    <span style="font-weight: 600;">VAT (7%):</span>
                                    <span id="vatAmount" style="font-weight: 700; color: var(--warning-color);">0.00</span>
                                </div>
                                <div style="display: flex; justify-content: space-between; padding: 15px 0; border-top: 3px solid #4caf50; background: rgba(76, 175, 80, 0.1); margin-top: 15px; border-radius: 8px; padding: 20px;">
                                    <span style="font-size: 20px; font-weight: 700; color: var(--success-color);">ยอดรวมที่ต้องชำระ:</span>
                                    <span id="totalAmount" style="font-size: 20px; font-weight: 700; color: var(--success-color);">0.00</span>
                                </div>
                            </div>
                        </div>
                        
                        <div style="display: flex; justify-content: flex-end; gap: 15px; margin-top: 30px;">
                            <button type="button" class="btn btn-secondary" onclick="clearForm()">
                                <span>🔄</span> ล้างข้อมูล
                            </button>
                            <button type="submit" class="btn btn-primary">
                                <span>💾</span> บันทึกข้อมูล
                            </button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Sales Document Page (New) -->
            <div id="sales-page" class="page-content" style="display: none;">
                <div class="main-header">
                    <h1 class="page-title">
                        <span>💰</span>
                        บันทึกเอกสารขาย
                    </h1>
                </div>
                
                <div class="form-container">
                    <form id="salesForm">
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>📝</span> ข้อมูลเอกสาร
                            </h3>
                            <div class="form-grid">
                                <div class="form-group">
                                    <label>วันที่เอกสาร <span style="color: red;">*</span></label>
                                    <input type="date" class="form-control" id="salesDocDate" required>
                                </div>
                                <div class="form-group">
                                    <label>เลขที่เอกสาร <span style="color: red;">*</span></label>
                                    <input type="text" class="form-control" placeholder="SO2025-001" required>
                                </div>
                                <div class="form-group">
                                    <label>ประเภทเอกสาร</label>
                                    <select class="form-control">
                                        <option value="invoice">ใบแจ้งหนี้/ใบกำกับภาษี</option>
                                        <option value="receipt">ใบเสร็จรับเงิน</option>
                                        <option value="quotation">ใบเสนอราคา</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>👤</span> ข้อมูลลูกค้า
                            </h3>
                            <div class="form-group">
                                <label>ชื่อลูกค้า <span style="color: red;">*</span></label>
                                <select class="form-control" onchange="updateCustomerInfo()" required>
                                    <option value="">-- เลือกลูกค้า --</option>
                                    <option value="1" data-address="123 ถ.สุขุมวิท กรุงเทพฯ" data-tax="0-1055-98765-43-2">[C001] บริษัท ABC จำกัด</option>
                                    <option value="2" data-address="456 ถ.พหลโยธิน กรุงเทพฯ" data-tax="-">[C002] ร้านสมใจ</option>
                                </select>
                            </div>
                            <div id="customerInfo" style="display: none; background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%); padding: 20px; border-radius: 12px; margin-top: 15px; border: 1px solid #e9ecef;">
                                <p style="margin: 5px 0; color: #666; font-size: 14px;">
                                    <strong>ที่อยู่:</strong> <span id="customerAddress">-</span>
                                </p>
                                <p style="margin: 5px 0; color: #666; font-size: 14px;">
                                    <strong>เลขประจำตัวผู้เสียภาษี:</strong> <span id="customerTax">-</span>
                                </p>
                            </div>
                        </div>
                        
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>📦</span> รายการสินค้า
                            </h3>
                            <div id="productList">
                                <div class="product-item" style="background: #f8f9fa; padding: 20px; border-radius: 12px; margin-bottom: 15px; border: 1px solid #e9ecef;">
                                    <div class="form-grid">
                                        <div class="form-group">
                                            <label>สินค้า</label>
                                            <select class="form-control product-select" onchange="updateProductInfo(this)">
                                                <option value="">-- เลือกสินค้า --</option>
                                                <option value="P001" data-price="220" data-unit="ถุง">P001 - ข้าวหอมมะลิ 5 กก.</option>
                                                <option value="P002" data-price="65" data-unit="ขวด">P002 - น้ำมันปาล์ม 1 ลิตร</option>
                                                <option value="P003" data-price="8" data-unit="ขวด">P003 - น้ำดื่ม 600 มล.</option>
                                            </select>
                                        </div>
                                        <div class="form-group">
                                            <label>จำนวน</label>
                                            <input type="number" class="form-control quantity-input" min="1" value="1" onchange="calculateLineTotal(this)">
                                        </div>
                                        <div class="form-group">
                                            <label>ราคาต่อหน่วย</label>
                                            <input type="number" class="form-control unit-price" step="0.01" readonly style="background: #f0f0f0;">
                                        </div>
                                        <div class="form-group">
                                            <label>หน่วย</label>
                                            <input type="text" class="form-control unit-text" readonly style="background: #f0f0f0;">
                                        </div>
                                        <div class="form-group">
                                            <label>รวมเงิน</label>
                                            <input type="number" class="form-control line-total" step="0.01" readonly style="background: #f0f0f0; font-weight: 600;">
                                        </div>
                                        <div class="form-group">
                                            <label>&nbsp;</label>
                                            <button type="button" class="btn btn-danger" onclick="removeProductLine(this)">
                                                <span>🗑️</span> ลบ
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <button type="button" class="btn btn-secondary" onclick="addProductLine()">
                                <span>➕</span> เพิ่มรายการสินค้า
                            </button>
                        </div>
                        
                        <div class="form-section">
                            <h3 class="section-title">
                                <span>🧮</span> สรุปยอดเงิน
                            </h3>
                            <div class="summary-box">
                                <div style="display: flex; justify-content: space-between; margin-bottom: 15px; padding: 10px 0; border-bottom: 1px solid #e9ecef;">
                                    <span style="font-weight: 600;">ยอดรวมก่อน VAT:</span>
                                    <span id="salesSubtotal" style="font-weight: 700; color: var(--primary-color);">0.00</span>
                                </div>
                                <div style="display: flex; justify-content: space-between; margin-bottom: 15px; padding: 10px 0; border-bottom: 1px solid #e9ecef;">
                                    <span style="font-weight: 600;">VAT (7%):</span>
                                    <span id="salesVat" style="font-weight: 700; color: var(--warning-color);">0.00</span>
                                </div>
                                <div style="display: flex; justify-content: space-between; padding: 15px 0; border-top: 3px solid #4caf50; background: rgba(76, 175, 80, 0.1); margin-top: 15px; border-radius: 8px; padding: 20px;">
                                    <span style="font-size: 20px; font-weight: 700; color: var(--success-color);">ยอดรวมทั้งสิ้น:</span>
                                    <span id="salesTotal" style="font-size: 20px; font-weight: 700; color: var(--success-color);">0.00</span>
                                </div>
                            </div>
                        </div>
                        
                        <div style="display: flex; justify-content: flex-end; gap: 15px; margin-top: 30px;">
                            <button type="button" class="btn btn-secondary" onclick="clearSalesForm()">
                                <span>🔄</span> ล้างข้อมูล
                            </button>
                            <button type="submit" class="btn btn-primary">
                                <span>💾</span> บันทึกข้อมูล
                            </button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Sales Summary Page (New) -->
            <div id="sales-summary-page" class="page-content" style="display: none;">
                <div class="main-header">
                    <h1 class="page-title">
                        <span>💰</span>
                        บันทึกยอดขาย
                    </h1>
                    <div class="header-actions">
                        <select class="form-control" style="width: 200px;">
                            <option>วันนี้</option>
                            <option>เมื่อวาน</option>
                            <option>สัปดาห์นี้</option>
                            <option>เดือนนี้</option>
                        </select>
                        <button class="btn btn-primary" onclick="showAddSalesSummary()">
                            <span>➕</span> เพิ่มยอดขาย
                        </button>
                    </div>
                </div>
                
                <!-- Summary Cards -->
                <div class="dashboard-grid" style="margin-bottom: 30px;">
                    <div class="stat-card">
                        <h3>ยอดขายวันนี้</h3>
                        <div class="stat-value">฿ 125,500</div>
                        <div class="stat-change">
                            <span>↑ 12%</span> จากเมื่อวาน
                        </div>
                    </div>
                    <div class="stat-card">
                        <h3>จำนวนบิลวันนี้</h3>
                        <div class="stat-value">47 บิล</div>
                        <div class="stat-change">
                            <span>เฉลี่ย ฿ 2,670</span> ต่อบิล
                        </div>
                    </div>
                    <div class="stat-card">
                        <h3>ยอดขายเดือนนี้</h3>
                        <div class="stat-value">฿ 1,285,000</div>
                        <div class="stat-change">
                            <span>↑ 8%</span> จากเดือนที่แล้ว
                        </div>
                    </div>
                    <div class="stat-card">
                        <h3>เป้าหมายเดือนนี้</h3>
                        <div class="stat-value">85.6%</div>
                        <div class="stat-change">
                            <span>เป้า ฿ 1,500,000</span>
                        </div>
                    </div>
                </div>

                <!-- Quick Entry Form -->
                <div class="form-container" style="margin-bottom: 30px;">
                    <div class="form-section">
                        <h3 class="section-title">
                            <span>⚡</span> บันทึกยอดขายด่วน
                        </h3>
                        <form id="quickSalesForm" style="background: none; padding: 0;">
                            <div class="form-grid">
                                <div class="form-group">
                                    <label>วันที่ขาย <span style="color: red;">*</span></label>
                                    <input type="date" class="form-control" id="salesDate" required>
                                </div>
                                <div class="form-group">
                                    <label>ช่วงเวลา</label>
                                    <select class="form-control">
                                        <option value="morning">เช้า (08:00-12:00)</option>
                                        <option value="afternoon">บ่าย (12:00-17:00)</option>
                                        <option value="evening">เย็น (17:00-20:00)</option>
                                        <option value="all">ทั้งวัน</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label>ยอดขายรวม <span style="color: red;">*</span></label>
                                    <input type="number" class="form-control" step="0.01" placeholder="0.00" required>
                                </div>
                                <div class="form-group">
                                    <label>จำนวนบิล</label>
                                    <input type="number" class="form-control" min="1" placeholder="1">
                                </div>
                                <div class="form-group">
                                    <label>หมายเหตุ</label>
                                    <input type="text" class="form-control" placeholder="เช่น โปรโมชั่น, เทศกาล">
                                </div>
                                <div class="form-group">
                                    <label>&nbsp;</label>
                                    <button type="submit" class="btn btn-primary">
                                        <span>💾</span> บันทึก
                                    </button>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>

                <!-- Sales History Table -->
                <div class="table-container">
                    <div class="table-header">
                        <h3 style="color: var(--primary-color); font-weight: 700;">📊 ประวัติยอดขาย</h3>
                        <div style="display: flex; gap: 10px;">
                            <div class="search-box">
                                <input type="text" placeholder="ค้นหาตามวันที่หรือหมายเหตุ...">
                            </div>
                            <button class="btn btn-success btn-sm">
                                <span>📊</span> Export
                            </button>
                        </div>
                    </div>
                    <table>
                        <thead>
                            <tr>
                                <th>วันที่</th>
                                <th>ช่วงเวลา</th>
                                <th>ยอดขาย</th>
                                <th>จำนวนบิล</th>
                                <th>ยอดเฉลี่ย/บิล</th>
                                <th>เปอร์เซ็นต์จากเป้า</th>
                                <th>หมายเหตุ</th>
                                <th>การดำเนินการ</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>09/01/2025</td>
                                <td><span class="badge badge-info">ทั้งวัน</span></td>
                                <td style="font-weight: 600; color: var(--success-color);">฿ 125,500</td>
                                <td style="text-align: center;">47</td>
                                <td style="text-align: right;">฿ 2,670</td>
                                <td style="text-align: center;">
                                    <span class="badge badge-success">8.4%</span>
                                </td>
                                <td>ปกติ</td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editSalesRecord('20250109')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="viewSalesDetail('20250109')">👁️</button>
                                </td>
                            </tr>
                            <tr>
                                <td>08/01/2025</td>
                                <td><span class="badge badge-warning">เช้า</span></td>
                                <td style="font-weight: 600; color: var(--success-color);">฿ 65,200</td>
                                <td style="text-align: center;">28</td>
                                <td style="text-align: right;">฿ 2,329</td>
                                <td style="text-align: center;">
                                    <span class="badge badge-success">4.3%</span>
                                </td>
                                <td>-</td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editSalesRecord('20250108_morning')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="viewSalesDetail('20250108_morning')">👁️</button>
                                </td>
                            </tr>
                            <tr>
                                <td>08/01/2025</td>
                                <td><span class="badge badge-info">บ่าย</span></td>
                                <td style="font-weight: 600; color: var(--success-color);">฿ 78,800</td>
                                <td style="text-align: center;">35</td>
                                <td style="text-align: right;">฿ 2,251</td>
                                <td style="text-align: center;">
                                    <span class="badge badge-success">5.3%</span>
                                </td>
                                <td>โปรโมชั่นสินค้า</td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editSalesRecord('20250108_afternoon')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="viewSalesDetail('20250108_afternoon')">👁️</button>
                                </td>
                            </tr>
                            <tr>
                                <td>07/01/2025</td>
                                <td><span class="badge badge-info">ทั้งวัน</span></td>
                                <td style="font-weight: 600; color: var(--success-color);">฿ 112,300</td>
                                <td style="text-align: center;">42</td>
                                <td style="text-align: right;">฿ 2,674</td>
                                <td style="text-align: center;">
                                    <span class="badge badge-success">7.5%</span>
                                </td>
                                <td>ปกติ</td>
                                <td>
                                    <button class="btn btn-sm" style="background: #f39c12; color: white;" onclick="editSalesRecord('20250107')">✏️</button>
                                    <button class="btn btn-sm" style="background: #3498db; color: white;" onclick="viewSalesDetail('20250107')">👁️</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Continue with other pages... -->
            <!-- (Previous pages remain the same, just with enhanced styling) -->
            
        </main>
    </div>
    
    <script>
        // Global functions
        window.toggleSidebar = toggleSidebar;
        window.showPage = showPage;
        window.toggleNavSection = toggleNavSection;
        window.togglePaymentDetails = togglePaymentDetails;
        window.togglePaymentStatusDetails = togglePaymentStatusDetails;
        window.selectPaymentStatus = selectPaymentStatus;
        window.updateSupplierInfo = updateSupplierInfo;
        window.updateCustomerInfo = updateCustomerInfo;
        window.updateBankAccountInfo = updateBankAccountInfo;
        window.calculateVAT = calculateVAT;
        window.clearForm = clearForm;
        window.clearSalesForm = clearSalesForm;
        window.showAddProduct = showAddProduct;
        window.showAddSupplier = showAddSupplier;
        window.showAddSalesSummary = showAddSalesSummary;
        window.editProduct = editProduct;
        window.adjustStock = adjustStock;
        window.editSupplier = editSupplier;
        window.viewSupplierHistory = viewSupplierHistory;
        window.viewBankAccounts = viewBankAccounts;
        window.markChequeCleared = markChequeCleared;
        window.editSalesRecord = editSalesRecord;
        window.viewSalesDetail = viewSalesDetail;
        window.updateProductInfo = updateProductInfo;
        window.calculateLineTotal = calculateLineTotal;
        window.addProductLine = addProductLine;
        window.removeProductLine = removeProductLine;
        window.closeModal = closeModal;
        window.toggleDueDateInput = toggleDueDateInput;
        window.addBankAccount = addBankAccount;
        window.removeBankAccount = removeBankAccount;
        window.saveSupplier = saveSupplier;
        window.showToast = showToast;

        // Mock database for suppliers
        let suppliersDB = {
            "00001": {
                code: "00001",
                nickname: "ทวีวงษ์",
                fullName: "บริษัท ทวีวงษ์อุตสาหกรรม จำกัด",
                paymentEntity: "company",
                taxId: "0-1055-12345-67-8",
                address: "123 ถ.สุขุมวิท แขวงคลองตัน เขตคลองตัน กรุงเทพฯ 10110",
                phone: "02-123-4567",
                paymentTerms: "due_date",
                dueDays: 30,
                bankAccounts: [
                    {bank: 'ธนาคารกรุงเทพ', number: '123-4-56789-0', name: 'บริษัท ทวีวงษ์อุตสาหกรรม จำกัด', isPrimary: true},
                    {bank: 'ธนาคารกสิกรไทย', number: '098-7-65432-1', name: 'บริษัท ทวีวงษ์อุตสาหกรรม จำกัด', isPrimary: false},
                    {bank: 'ธนาคารไทยพาณิชย์', number: '555-5-55555-5', name: 'บริษัท ทวีวงษ์อุตสาหกรรม จำกัด', isPrimary: false}
                ]
            },
            "00002": {
                code: "00002",
                nickname: "สมชาย",
                fullName: "คุณสมชาย ใจดี",
                paymentEntity: "wipaporn",
                taxId: "",
                address: "456 ถ.พหลโยธิน แขวงลาดยาว เขตจตุจักร กรุงเทพฯ 10900",
                phone: "081-234-5678",
                paymentTerms: "cash_cheque",
                dueDays: 0,
                bankAccounts: []
            },
            "00003": {
                code: "00003",
                nickname: "ABC Supply",
                fullName: "บริษัท ABC ซัพพลาย จำกัด",
                paymentEntity: "company",
                taxId: "0-1055-98765-43-2",
                address: "789 ถ.รัชดาภิเษก แขวงหวยขวาง เขตหวยขวาง กรุงเทพฯ 10310",
                phone: "02-987-6543",
                paymentTerms: "monday",
                dueDays: 0,
                bankAccounts: [
                    {bank: 'ธนาคารกสิกรไทย', number: '111-1-11111-1', name: 'บริษัท ABC ซัพพลาย จำกัด', isPrimary: true},
                    {bank: 'ธนาคารกรุงไทย', number: '222-2-22222-2', name: 'บริษัท ABC ซัพพลาย จำกัด', isPrimary: false}
                ]
            }
        };

        // Toggle sidebar for mobile
        function toggleSidebar() {
            const sidebar = document.getElementById('sidebar');
            if (sidebar) {
                sidebar.classList.toggle('active');
            }
        }

        // Toggle navigation section (for development section)
        function toggleNavSection(sectionId) {
            const section = document.getElementById(sectionId + '-section');
            const header = event.currentTarget;
            
            if (section) {
                if (section.style.display === 'none' || !section.style.display) {
                    section.style.display = 'block';
                    header.classList.add('active');
                } else {
                    section.style.display = 'none';
                    header.classList.remove('active');
                }
            }
        }

        // Show page
        function showPage(page, navElement) {
            // Hide all pages
            document.querySelectorAll('.page-content').forEach(p => p.style.display = 'none');
            
            // Show selected page
            const selectedPage = document.getElementById(page + '-page');
            if (selectedPage) {
                selectedPage.style.display = 'block';
            }
            
            // Update active nav - handle both main nav and sub nav
            document.querySelectorAll('.nav-item, .nav-sub-item').forEach(item => item.classList.remove('active'));
            if (navElement) {
                navElement.classList.add('active');
                
                // If it's a sub-item, also open the parent section
                if (navElement.classList.contains('nav-sub-item')) {
                    const section = navElement.closest('.nav-section-content');
                    const header = section?.previousElementSibling;
                    if (section && header) {
                        section.style.display = 'block';
                        header.classList.add('active');
                    }
                }
            }
            
            // Close mobile menu
            if (window.innerWidth <= 768) {
                const sidebar = document.getElementById('sidebar');
                if (sidebar) sidebar.classList.remove('active');
            }
        }

        // Select payment status with visual feedback
        function selectPaymentStatus(labelElement, status) {
            // Remove selection from all labels
            document.querySelectorAll('label[onclick*="selectPaymentStatus"]').forEach(label => {
                label.style.borderColor = '#e9ecef';
                label.style.backgroundColor = 'white';
            });
            
            // Highlight selected label
            labelElement.style.borderColor = 'var(--mahachai-orange)';
            labelElement.style.backgroundColor = 'rgba(255, 138, 66, 0.1)';
        }

        // Toggle payment status details
        function togglePaymentStatusDetails() {
            const selectedStatus = document.querySelector('input[name="paymentStatus"]:checked');
            const paymentMethodSection = document.getElementById('paymentMethodSection');
            const dueDateInfo = document.getElementById('dueDateInfo');
            
            // Hide all sections first
            if (paymentMethodSection) paymentMethodSection.style.display = 'none';
            if (dueDateInfo) dueDateInfo.style.display = 'none';
            
            if (selectedStatus) {
                const status = selectedStatus.value;
                
                if (status === 'paid' && paymentMethodSection) {
                    paymentMethodSection.style.display = 'block';
                } else if ((status === 'pending_bill' || status === 'weekly_transfer') && dueDateInfo) {
                    dueDateInfo.style.display = 'block';
                    calculateExpectedDueDate(status);
                }
            }
            
            // Clear payment method selection when switching status
            document.querySelectorAll('input[name="paymentMethod"]').forEach(radio => radio.checked = false);
            togglePaymentDetails();
        }

        // Calculate expected due date based on supplier terms
        function calculateExpectedDueDate(status) {
            const supplierSelect = document.querySelector('select[onchange="updateSupplierInfo()"]');
            const expectedDueDateInput = document.getElementById('expectedDueDate');
            
            if (supplierSelect && expectedDueDateInput && supplierSelect.value) {
                const supplier = suppliersDB[supplierSelect.value];
                if (supplier) {
                    const today = new Date();
                    let dueDate = new Date(today);
                    
                    if (status === 'pending_bill') {
                        if (supplier.paymentTerms === 'due_date') {
                            dueDate.setDate(today.getDate() + supplier.dueDays);
                        } else if (supplier.paymentTerms === 'monday') {
                            // Next Monday
                            const daysToMonday = (1 + 7 - today.getDay()) % 7 || 7;
                            dueDate.setDate(today.getDate() + daysToMonday);
                        }
                    } else if (status === 'weekly_transfer') {
                        // Next Monday for weekly transfer
                        const daysToMonday = (1 + 7 - today.getDay()) % 7 || 7;
                        dueDate.setDate(today.getDate() + daysToMonday);
                    }
                    
                    expectedDueDateInput.value = dueDate.toISOString().split('T')[0];
                }
            }
        }

        // Toggle payment details
        function togglePaymentDetails() {
            const chequeDetails = document.getElementById('chequeDetails');
            const transferDetails = document.getElementById('transferDetails');
            const selectedPayment = document.querySelector('input[name="paymentMethod"]:checked');
            
            if (chequeDetails) chequeDetails.style.display = 'none';
            if (transferDetails) transferDetails.style.display = 'none';
            
            if (selectedPayment) {
                if (selectedPayment.value === 'cheque' && chequeDetails) {
                    chequeDetails.style.display = 'block';
                } else if (selectedPayment.value === 'transfer' && transferDetails) {
                    transferDetails.style.display = 'block';
                    loadSupplierBankAccounts();
                }
            }
        }

        // Load supplier bank accounts
        function loadSupplierBankAccounts() {
            const supplierSelect = document.querySelector('select[onchange="updateSupplierInfo()"]');
            const bankAccountSelect = document.getElementById('supplierBankAccount');
            
            if (supplierSelect && bankAccountSelect && supplierSelect.value) {
                const supplier = suppliersDB[supplierSelect.value];
                
                bankAccountSelect.innerHTML = '<option value="">-- เลือกบัญชีธนาคาร --</option>';
                
                if (supplier && supplier.bankAccounts.length > 0) {
                    supplier.bankAccounts.forEach((account, index) => {
                        const option = document.createElement('option');
                        option.value = index;
                        option.setAttribute('data-bank', account.bank);
                        option.setAttribute('data-number', account.number);
                        option.setAttribute('data-name', account.name);
                        option.textContent = `${account.bank} - ${account.number}` + (account.isPrimary ? ' (หลัก)' : '');
                        bankAccountSelect.appendChild(option);
                    });
                } else {
                    const option = document.createElement('option');
                    option.value = "";
                    option.textContent = "Supplier นี้ยังไม่มีข้อมูลบัญชีธนาคาร";
                    option.disabled = true;
                    bankAccountSelect.appendChild(option);
                }
            }
        }

        // Update bank account info
        function updateBankAccountInfo() {
            const select = event.target;
            const selectedOption = select.options[select.selectedIndex];
            const bankAccountInfo = document.getElementById('bankAccountInfo');
            const bankNameEl = document.getElementById('bankName');
            const accountNumberEl = document.getElementById('accountNumber');
            const accountNameEl = document.getElementById('accountName');
            
            if (select.value && bankAccountInfo && bankNameEl && accountNumberEl && accountNameEl) {
                bankNameEl.textContent = selectedOption.dataset.bank || '-';
                accountNumberEl.textContent = selectedOption.dataset.number || '-';
                accountNameEl.textContent = selectedOption.dataset.name || '-';
                bankAccountInfo.style.display = 'block';
            } else if (bankAccountInfo) {
                bankAccountInfo.style.display = 'none';
            }
        }

        // Update supplier info
        function updateSupplierInfo() {
            const select = event.target;
            const supplierId = select.value;
            const supplierInfo = document.getElementById('supplierInfo');
            const payeeInfo = document.getElementById('payeeInfo');
            const paymentInfo = document.getElementById('paymentInfo');
            
            if (supplierId && supplierInfo && payeeInfo && paymentInfo) {
                const supplier = suppliersDB[supplierId];
                if (supplier) {
                    payeeInfo.textContent = supplier.paymentEntity === 'company' ? 'บริษัท' : 'วิภาภรณ์';
                    
                    let paymentText = '';
                    switch(supplier.paymentTerms) {
                        case 'due_date':
                            paymentText = `Due date (${supplier.dueDays} วัน)`;
                            break;
                        case 'monday':
                            paymentText = 'ชำระทุกวันจันทร์';
                            break;
                        case 'cash_cheque':
                            paymentText = 'เงินสด/เช็ค';
                            break;
                        case 'next_bill':
                            paymentText = 'เรียกทุกบิลถัดไป';
                            break;
                    }
                    paymentInfo.textContent = paymentText;
                    supplierInfo.style.display = 'block';
                    
                    // Update expected due date if relevant
                    const selectedStatus = document.querySelector('input[name="paymentStatus"]:checked');
                    if (selectedStatus && (selectedStatus.value === 'pending_bill' || selectedStatus.value === 'weekly_transfer')) {
                        calculateExpectedDueDate(selectedStatus.value);
                    }
                }
            } else if (supplierInfo) {
                supplierInfo.style.display = 'none';
            }
        }

        // Update customer info
        function updateCustomerInfo() {
            const select = event.target;
            const selectedOption = select.options[select.selectedIndex];
            const customerInfo = document.getElementById('customerInfo');
            const customerAddress = document.getElementById('customerAddress');
            const customerTax = document.getElementById('customerTax');
            
            if (selectedOption && selectedOption.value && customerInfo && customerAddress && customerTax) {
                customerAddress.textContent = selectedOption.dataset.address || '-';
                customerTax.textContent = selectedOption.dataset.tax || '-';
                customerInfo.style.display = 'block';
            } else if (customerInfo) {
                customerInfo.style.display = 'none';
            }
        }

        // Calculate VAT
        function calculateVAT() {
            const amountInput = document.getElementById('beforeVat');
            const amount = parseFloat(amountInput?.value) || 0;
            const vatType = document.querySelector('input[name="vatType"]:checked');
            const subtotalEl = document.getElementById('subtotal');
            const vatAmountEl = document.getElementById('vatAmount');
            const totalAmountEl = document.getElementById('totalAmount');
            
            if (subtotalEl && vatAmountEl && totalAmountEl) {
                let vatAmount = 0;
                let totalAmount = amount;
                
                if (vatType && vatType.value === 'vat') {
                    vatAmount = amount * 0.07;
                    totalAmount = amount + vatAmount;
                }
                
                subtotalEl.textContent = '฿ ' + amount.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
                vatAmountEl.textContent = '฿ ' + vatAmount.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
                totalAmountEl.textContent = '฿ ' + totalAmount.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            }
        }

        // Clear form
        function clearForm() {
            if (confirm('ต้องการล้างข้อมูลทั้งหมดใช่หรือไม่?')) {
                const form = document.getElementById('purchaseForm');
                if (form) form.reset();
                
                const elements = ['chequeDetails', 'transferDetails', 'supplierInfo', 'paymentMethodSection', 'dueDateInfo', 'bankAccountInfo'];
                elements.forEach(id => {
                    const el = document.getElementById(id);
                    if (el) el.style.display = 'none';
                });
                
                // Reset payment status styling
                document.querySelectorAll('label[onclick*="selectPaymentStatus"]').forEach(label => {
                    label.style.borderColor = '#e9ecef';
                    label.style.backgroundColor = 'white';
                });
                
                const calculations = ['subtotal', 'vatAmount', 'totalAmount'];
                calculations.forEach(id => {
                    const el = document.getElementById(id);
                    if (el) el.textContent = '฿ 0.00';
                });
                
                const today = new Date().toISOString().split('T')[0];
                const recordDate = document.getElementById('recordDate');
                if (recordDate) recordDate.value = today;
                
                showToast('ล้างข้อมูลเรียบร้อยแล้ว', 'success');
            }
        }

        // Clear sales form
        function clearSalesForm() {
            if (confirm('ต้องการล้างข้อมูลทั้งหมดใช่หรือไม่?')) {
                const form = document.getElementById('salesForm');
                if (form) form.reset();
                
                const productList = document.getElementById('productList');
                if (productList) {
                    const firstItem = productList.querySelector('.product-item');
                    productList.innerHTML = '';
                    if (firstItem) {
                        firstItem.querySelectorAll('input, select').forEach(input => {
                            if (input.type !== 'button') input.value = '';
                        });
                        productList.appendChild(firstItem);
                    }
                }
                
                calculateSalesTotal();
                showToast('ล้างข้อมูลเรียบร้อยแล้ว', 'success');
            }
        }

        // Management functions
        function showAddProduct() { alert('เปิดหน้าต่างเพิ่มสินค้าใหม่'); }
        function showAddSalesSummary() { alert('เปิดหน้าต่างเพิ่มยอดขายใหม่'); }
        function editProduct(productId) { alert('แก้ไขสินค้า: ' + productId); }
        function adjustStock(productId) { alert('ปรับสต็อกสินค้า: ' + productId); }
        function editSalesRecord(recordId) { alert('แก้ไขยอดขาย: ' + recordId); }
        function viewSalesDetail(recordId) { alert('ดูรายละเอียดยอดขาย: ' + recordId); }

        // Supplier management functions
        function showAddSupplier() {
            console.log('showAddSupplier called'); // Debug
            
            // Generate next supplier code
            const nextCode = generateNextSupplierCode();
            const codeInput = document.getElementById('supplierCode');
            const modalTitle = document.getElementById('supplierModalTitle');
            const form = document.getElementById('supplierForm');
            const modal = document.getElementById('addSupplierModal');
            
            if (!modal) {
                console.error('Modal not found');
                return;
            }
            
            // Set title and code
            if (modalTitle) modalTitle.textContent = 'เพิ่มข้อมูล Supplier';
            if (codeInput) codeInput.value = nextCode;
            
            // Clear form
            if (form) form.reset();
            if (codeInput) codeInput.value = nextCode; // Set again after reset
            
            // Clear bank accounts list
            const bankAccountsList = document.getElementById('bankAccountsList');
            if (bankAccountsList) {
                bankAccountsList.innerHTML = '';
                bankAccountCount = 0;
            }
            
            // Add one empty bank account row
            addBankAccount();
            
            // Show modal
            modal.classList.add('active');
            console.log('Modal should be visible now'); // Debug
        }

        function editSupplier(code) {
            console.log('editSupplier called for:', code); // Debug
            
            const supplier = suppliersDB[code];
            if (!supplier) {
                showToast('ไม่พบข้อมูล Supplier', 'error');
                return;
            }
            
            const modal = document.getElementById('addSupplierModal');
            if (!modal) {
                console.error('Modal not found');
                return;
            }
            
            // Set title
            const modalTitle = document.getElementById('supplierModalTitle');
            if (modalTitle) modalTitle.textContent = 'แก้ไขข้อมูล Supplier';
            
            // Fill form with supplier data
            const fields = {
                'supplierCode': supplier.code,
                'supplierNickname': supplier.nickname,
                'supplierFullName': supplier.fullName,
                'paymentEntity': supplier.paymentEntity,
                'supplierTaxId': supplier.taxId,
                'supplierAddress': supplier.address,
                'supplierPhone': supplier.phone
            };
            
            Object.entries(fields).forEach(([id, value]) => {
                const element = document.getElementById(id);
                if (element) element.value = value || '';
            });
            
            // Set payment terms
            const paymentRadio = document.querySelector(`input[name="paymentTerms"][value="${supplier.paymentTerms}"]`);
            if (paymentRadio) {
                paymentRadio.checked = true;
                if (supplier.paymentTerms === 'due_date') {
                    const dueDateInput = document.getElementById('dueDateInput');
                    const dueDaysInput = document.getElementById('dueDays');
                    if (dueDateInput) dueDateInput.style.display = 'block';
                    if (dueDaysInput) dueDaysInput.value = supplier.dueDays;
                }
                toggleDueDateInput(); // Update styling
            }
            
            // Fill bank accounts
            const bankAccountsList = document.getElementById('bankAccountsList');
            if (bankAccountsList) {
                bankAccountsList.innerHTML = '';
                bankAccountCount = 0;
                
                if (supplier.bankAccounts && supplier.bankAccounts.length > 0) {
                    supplier.bankAccounts.forEach(account => {
                        addBankAccount(account);
                    });
                } else {
                    addBankAccount();
                }
            }
            
            // Show modal
            modal.classList.add('active');
        }

        function generateNextSupplierCode() {
            const codes = Object.keys(suppliersDB).map(code => parseInt(code));
            const maxCode = Math.max(...codes, 0);
            return String(maxCode + 1).padStart(5, '0');
        }

        function viewSupplierHistory(code) {
            showToast(`ดูประวัติการซื้อ Supplier รหัส: ${code}`, 'info');
        }

        function viewBankAccounts(code) {
            console.log('viewBankAccounts called for:', code); // Debug
            
            const supplier = suppliersDB[code];
            if (!supplier) {
                showToast('ไม่พบข้อมูล Supplier', 'error');
                return;
            }
            
            const modal = document.getElementById('bankAccountsModal');
            const supplierNameEl = document.getElementById('supplierNameInModal');
            const listView = document.getElementById('bankAccountsListView');
            
            if (!modal || !supplierNameEl || !listView) {
                console.error('Bank accounts modal elements not found');
                return;
            }
            
            supplierNameEl.textContent = supplier.fullName;
            
            let html = '';
            if (supplier.bankAccounts && supplier.bankAccounts.length > 0) {
                supplier.bankAccounts.forEach((account, index) => {
                    const borderStyle = account.isPrimary ? 'border: 2px solid #27ae60;' : '';
                    const primaryBadge = account.isPrimary ? '<span class="badge badge-success" style="float: right;">บัญชีหลัก</span>' : '';
                    
                    html += `<div style="background: #f8f9fa; padding: 20px; border-radius: 12px; margin-bottom: 15px; ${borderStyle}">`;
                    html += primaryBadge;
                    html += `<h4 style="margin: 0 0 15px 0; color: var(--primary-color);">${account.bank}</h4>`;
                    html += `<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 10px;">`;
                    html += `<p style="margin: 5px 0;"><strong>เลขที่บัญชี:</strong> ${account.number}</p>`;
                    html += `<p style="margin: 5px 0;"><strong>ชื่อบัญชี:</strong> ${account.name}</p>`;
                    html += `</div></div>`;
                });
            } else {
                html = '<p style="text-align: center; color: #999; padding: 40px;">ไม่มีข้อมูลบัญชีธนาคาร</p>';
            }
            
            listView.innerHTML = html;
            modal.classList.add('active');
        }

        function markChequeCleared() { 
            if (confirm('ยืนยันว่าเช็คเคลียร์แล้ว?')) {
                showToast('อัปเดตสถานะเช็คเรียบร้อยแล้ว', 'success');
            }
        }

        // Due date input toggle
        function toggleDueDateInput() {
            const selectedPayment = document.querySelector('input[name="paymentTerms"]:checked');
            const dueDateInput = document.getElementById('dueDateInput');
            
            if (selectedPayment && selectedPayment.value === 'due_date') {
                dueDateInput.style.display = 'block';
            } else {
                dueDateInput.style.display = 'none';
            }
            
            // Update radio button styling
            document.querySelectorAll('label:has(input[name="paymentTerms"])').forEach(label => {
                const radio = label.querySelector('input[type="radio"]');
                if (radio.checked) {
                    label.style.borderColor = 'var(--mahachai-orange)';
                    label.style.backgroundColor = 'rgba(255, 138, 66, 0.1)';
                } else {
                    label.style.borderColor = '#e9ecef';
                    label.style.backgroundColor = 'white';
                }
            });
        }

        // Bank account management
        let bankAccountCount = 0;
        
        function addBankAccount(accountData = null) {
            console.log('addBankAccount called', accountData); // Debug
            
            const addBankBtn = document.getElementById('addBankBtn');
            const bankAccountsList = document.getElementById('bankAccountsList');
            
            if (!bankAccountsList) {
                console.error('bankAccountsList not found');
                return;
            }
            
            if (bankAccountCount >= 5) {
                showToast('สามารถเพิ่มบัญชีธนาคารได้สูงสุด 5 บัญชี', 'warning');
                return;
            }
            
            bankAccountCount++;
            
            const newAccount = document.createElement('div');
            newAccount.className = 'bank-account-item';
            newAccount.style = 'background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%); padding: 20px; border-radius: 12px; margin-bottom: 15px; position: relative; border: 1px solid #e9ecef;';
            
            newAccount.innerHTML = `
                ${bankAccountCount > 1 ? '<button type="button" onclick="removeBankAccount(this)" style="position: absolute; top: 15px; right: 15px; background: #e74c3c; color: white; border: none; padding: 8px 12px; border-radius: 6px; cursor: pointer; font-size: 12px;">ลบ</button>' : ''}
                <div class="form-grid">
                    <div class="form-group">
                        <label>ธนาคาร</label>
                        <select class="form-control bank-select">
                            <option value="">-- เลือกธนาคาร --</option>
                            <option value="ธนาคารกรุงเทพ">ธนาคารกรุงเทพ</option>
                            <option value="ธนาคารกสิกรไทย">ธนาคารกสิกรไทย</option>
                            <option value="ธนาคารไทยพาณิชย์">ธนาคารไทยพาณิชย์</option>
                            <option value="ธนาคารกรุงไทย">ธนาคารกรุงไทย</option>
                            <option value="ธนาคารกรุงศรีอยุธยา">ธนาคารกรุงศรีอยุธยา</option>
                            <option value="ธนาคารทหารไทยธนชาต">ธนาคารทหารไทยธนชาต</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>เลขที่บัญชี</label>
                        <input type="text" class="form-control account-number" placeholder="000-0-00000-0">
                    </div>
                    <div class="form-group">
                        <label>ชื่อบัญชี</label>
                        <input type="text" class="form-control account-name" placeholder="ชื่อบัญชีตามสมุดบัญชี">
                    </div>
                    <div class="form-group">
                        <label style="display: flex; align-items: center; gap: 8px; cursor: pointer; font-weight: normal;">
                            <input type="checkbox" class="primary-checkbox" onchange="setPrimaryAccount(this)"> 
                            <span>บัญชีหลัก</span>
                        </label>
                    </div>
                </div>
            `;
            
            bankAccountsList.appendChild(newAccount);
            
            // Fill data if provided
            if (accountData) {
                const bankSelect = newAccount.querySelector('.bank-select');
                const accountNumber = newAccount.querySelector('.account-number');
                const accountName = newAccount.querySelector('.account-name');
                const primaryCheck = newAccount.querySelector('.primary-checkbox');
                
                if (bankSelect) bankSelect.value = accountData.bank || '';
                if (accountNumber) accountNumber.value = accountData.number || '';
                if (accountName) accountName.value = accountData.name || '';
                if (primaryCheck) primaryCheck.checked = accountData.isPrimary || false;
            }
            
            // Update add button
            if (addBankBtn) {
                if (bankAccountCount >= 5) {
                    addBankBtn.disabled = true;
                    addBankBtn.innerHTML = '<span>🔒</span> ถึงขีดจำกัดแล้ว (5 บัญชี)';
                } else {
                    addBankBtn.disabled = false;
                    addBankBtn.innerHTML = '<span>➕</span> เพิ่มบัญชีธนาคาร';
                }
            }
            
            console.log('Bank account added, count:', bankAccountCount);
        }
        
        function removeBankAccount(button) {
            console.log('removeBankAccount called'); // Debug
            
            if (bankAccountCount <= 1) {
                showToast('ต้องมีบัญชีธนาคารอย่างน้อย 1 บัญชี', 'warning');
                return;
            }
            
            if (button && button.parentElement) {
                button.parentElement.remove();
                bankAccountCount--;
                
                const addBankBtn = document.getElementById('addBankBtn');
                if (addBankBtn) {
                    addBankBtn.disabled = false;
                    addBankBtn.innerHTML = '<span>➕</span> เพิ่มบัญชีธนาคาร';
                }
                
                console.log('Bank account removed, count:', bankAccountCount);
            }
        }
        
        function setPrimaryAccount(checkbox) {
            if (checkbox && checkbox.checked) {
                // Uncheck all other primary checkboxes
                const allPrimaryCheckboxes = document.querySelectorAll('.bank-account-item .primary-checkbox');
                allPrimaryCheckboxes.forEach(cb => {
                    if (cb !== checkbox) cb.checked = false;
                });
            }
        }

        // Modal management
        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        // Save supplier
        function saveSupplier() {
            const form = document.getElementById('supplierForm');
            const formData = new FormData(form);
            
            // Basic validation
            const requiredFields = ['supplierNickname', 'supplierFullName', 'paymentEntity', 'supplierAddress', 'supplierPhone'];
            for (const field of requiredFields) {
                const value = document.getElementById(field).value.trim();
                if (!value) {
                    showToast(`กรุณากรอก${document.querySelector(`label[for="${field}"], label`).textContent}`, 'error');
                    return;
                }
            }
            
            // Check payment terms
            const paymentTerms = document.querySelector('input[name="paymentTerms"]:checked');
            if (!paymentTerms) {
                showToast('กรุณาเลือกลักษณะการรับเงิน', 'error');
                return;
            }
            
            // Validate due days if needed
            if (paymentTerms.value === 'due_date') {
                const dueDays = document.getElementById('dueDays').value;
                if (!dueDays || dueDays < 1) {
                    showToast('กรุณาระบุจำนวนวันสำหรับ Due date', 'error');
                    return;
                }
            }
            
            // Collect bank accounts
            const bankAccounts = [];
            document.querySelectorAll('.bank-account-item').forEach(item => {
                const bank = item.querySelector('.bank-select').value;
                const number = item.querySelector('.account-number').value.trim();
                const name = item.querySelector('.account-name').value.trim();
                const isPrimary = item.querySelector('.primary-checkbox').checked;
                
                if (bank && number && name) {
                    bankAccounts.push({ bank, number, name, isPrimary });
                }
            });
            
            // Create supplier object
            const supplierCode = document.getElementById('supplierCode').value;
            const supplierData = {
                code: supplierCode,
                nickname: document.getElementById('supplierNickname').value.trim(),
                fullName: document.getElementById('supplierFullName').value.trim(),
                paymentEntity: document.getElementById('paymentEntity').value,
                taxId: document.getElementById('supplierTaxId').value.trim(),
                address: document.getElementById('supplierAddress').value.trim(),
                phone: document.getElementById('supplierPhone').value.trim(),
                paymentTerms: paymentTerms.value,
                dueDays: paymentTerms.value === 'due_date' ? parseInt(document.getElementById('dueDays').value) : 0,
                bankAccounts: bankAccounts
            };
            
            // Save to mock database
            suppliersDB[supplierCode] = supplierData;
            
            // Update supplier select in purchase form
            updateSupplierSelectOptions();
            
            closeModal('addSupplierModal');
            showToast('บันทึกข้อมูล Supplier เรียบร้อยแล้ว', 'success');
            
            // Refresh supplier page if currently viewing
            if (document.getElementById('supplier-page').style.display !== 'none') {
                setTimeout(() => {
                    location.reload(); // In real app, would refresh the table
                }, 1000);
            }
        }

        // Update supplier select options in purchase form
        function updateSupplierSelectOptions() {
            const supplierSelect = document.querySelector('select[onchange="updateSupplierInfo()"]');
            if (!supplierSelect) return;
            
            // Clear existing options except the first one
            supplierSelect.innerHTML = '<option value="">-- เลือกผู้ขาย --</option>';
            
            // Add updated options
            Object.values(suppliersDB).forEach(supplier => {
                const option = document.createElement('option');
                option.value = supplier.code;
                option.textContent = `[${supplier.code}] ${supplier.nickname} - ${supplier.fullName}`;
                supplierSelect.appendChild(option);
            });
        }

        // Sales form functions (for development section)
        function updateProductInfo(selectElement) {
            const selectedOption = selectElement.options[selectElement.selectedIndex];
            const productItem = selectElement.closest('.product-item');
            
            if (selectedOption && selectedOption.value && productItem) {
                const priceInput = productItem.querySelector('.unit-price');
                const unitInput = productItem.querySelector('.unit-text');
                const quantityInput = productItem.querySelector('.quantity-input');
                
                if (priceInput) priceInput.value = selectedOption.dataset.price || 0;
                if (unitInput) unitInput.value = selectedOption.dataset.unit || '';
                if (quantityInput) quantityInput.value = 1;
                
                calculateLineTotal(quantityInput || priceInput);
            }
        }

        function calculateLineTotal(inputElement) {
            const productItem = inputElement.closest('.product-item');
            
            if (productItem) {
                const quantity = parseFloat(productItem.querySelector('.quantity-input')?.value) || 0;
                const unitPrice = parseFloat(productItem.querySelector('.unit-price')?.value) || 0;
                const lineTotalInput = productItem.querySelector('.line-total');
                
                if (lineTotalInput) {
                    const lineTotal = quantity * unitPrice;
                    lineTotalInput.value = lineTotal.toFixed(2);
                }
            }
            
            calculateSalesTotal();
        }

        function calculateSalesTotal() {
            const productItems = document.querySelectorAll('.product-item');
            let subtotal = 0;
            
            productItems.forEach(item => {
                const lineTotal = parseFloat(item.querySelector('.line-total')?.value) || 0;
                subtotal += lineTotal;
            });
            
            const vat = subtotal * 0.07;
            const total = subtotal + vat;
            
            const subtotalEl = document.getElementById('salesSubtotal');
            const vatEl = document.getElementById('salesVat');
            const totalEl = document.getElementById('salesTotal');
            
            if (subtotalEl) subtotalEl.textContent = '฿ ' + subtotal.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            if (vatEl) vatEl.textContent = '฿ ' + vat.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            if (totalEl) totalEl.textContent = '฿ ' + total.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }

        function addProductLine() {
            const productList = document.getElementById('productList');
            const firstItem = document.querySelector('.product-item');
            
            if (productList && firstItem) {
                const newItem = firstItem.cloneNode(true);
                newItem.querySelectorAll('input, select').forEach(input => {
                    if (input.type !== 'button') {
                        input.value = '';
                        if (input.classList.contains('quantity-input')) input.value = '1';
                    }
                });
                productList.appendChild(newItem);
            }
        }

        function removeProductLine(button) {
            const productItem = button.closest('.product-item');
            const productList = document.getElementById('productList');
            
            if (productItem && productList && productList.children.length > 1) {
                productItem.remove();
                calculateSalesTotal();
            } else {
                showToast('ต้องมีรายการสินค้าอย่างน้อย 1 รายการ', 'warning');
            }
        }

        // Toast notification
        function showToast(message, type = 'success') {
            const existingToast = document.querySelector('.toast');
            if (existingToast) existingToast.remove();
            
            const toast = document.createElement('div');
            toast.className = `toast ${type}`;
            toast.textContent = message;
            
            document.body.appendChild(toast);
            
            setTimeout(() => toast.classList.add('show'), 100);
            setTimeout(() => {
                toast.classList.remove('show');
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            console.log('DOM Content Loaded'); // Debug
            
            // Set today's date
            const today = new Date().toISOString().split('T')[0];
            const dateInputs = document.querySelectorAll('#recordDate, #docDate, #salesDocDate, #salesDate');
            dateInputs.forEach(input => {
                if (input && input.id === 'recordDate') {
                    input.value = today;
                } else if (input) {
                    input.value = today;
                }
            });

            // Initialize supplier select options in purchase form
            updateSupplierSelectOptions();

            // Add form submission handlers
            const purchaseForm = document.getElementById('purchaseForm');
            if (purchaseForm) {
                purchaseForm.addEventListener('submit', function(e) {
                    e.preventDefault();
                    
                    // Validation
                    const paymentStatus = document.querySelector('input[name="paymentStatus"]:checked');
                    if (!paymentStatus) {
                        showToast('กรุณาเลือกสถานะการชำระเงิน', 'error');
                        return;
                    }
                    
                    if (paymentStatus.value === 'paid') {
                        const paymentMethod = document.querySelector('input[name="paymentMethod"]:checked');
                        if (!paymentMethod) {
                            showToast('กรุณาเลือกลักษณะการชำระเงิน', 'error');
                            return;
                        }
                        
                        if (paymentMethod.value === 'transfer') {
                            const bankAccount = document.getElementById('supplierBankAccount');
                            if (!bankAccount?.value) {
                                showToast('กรุณาเลือกบัญชีธนาคารของ Supplier', 'error');
                                return;
                            }
                        }
                    }
                    
                    showToast('บันทึกเอกสารซื้อเรียบร้อยแล้ว', 'success');
                    setTimeout(() => clearForm(), 1500);
                });
            }

            const salesForm = document.getElementById('salesForm');
            if (salesForm) {
                salesForm.addEventListener('submit', function(e) {
                    e.preventDefault();
                    showToast('บันทึกเอกสารขายเรียบร้อยแล้ว', 'success');
                    setTimeout(() => clearSalesForm(), 1500);
                });
            }

            // Add quick sales form handler
            const quickSalesForm = document.getElementById('quickSalesForm');
            if (quickSalesForm) {
                quickSalesForm.addEventListener('submit', function(e) {
                    e.preventDefault();
                    showToast('บันทึกยอดขายเรียบร้อยแล้ว', 'success');
                    setTimeout(() => {
                        quickSalesForm.reset();
                        quickSalesForm.querySelector('#salesDate').value = today;
                    }, 1500);
                });
            }

            // Add event listeners for payment terms radio buttons
            document.addEventListener('change', function(e) {
                if (e.target.name === 'paymentTerms') {
                    console.log('Payment terms changed:', e.target.value); // Debug
                    toggleDueDateInput();
                }
            });

            // Add click event listener for modal close buttons
            document.addEventListener('click', function(e) {
                // Close modal when clicking outside
                if (e.target.classList.contains('modal')) {
                    const modals = ['addSupplierModal', 'bankAccountsModal'];
                    modals.forEach(modalId => {
                        if (e.target.id === modalId) {
                            closeModal(modalId);
                        }
                    });
                }
            });

            // Initialize sales total calculation if on sales page
            if (document.getElementById('salesTotal')) {
                calculateSalesTotal();
            }

            // Test supplier modal functionality
            console.log('Testing modal elements:');
            console.log('addSupplierModal:', document.getElementById('addSupplierModal') ? 'Found' : 'Not found');
            console.log('supplierForm:', document.getElementById('supplierForm') ? 'Found' : 'Not found');
            console.log('bankAccountsList:', document.getElementById('bankAccountsList') ? 'Found' : 'Not found');
            
            console.log('Initialization complete');
        });
    </script>
</body>
</html>
