/**
 * ============================================================
 *  DABAN BOOKKEEPING APP
 *  A full-featured bookkeeping system for Daban Clothing & Apparel
 *
 *  Architecture Overview:
 *  ─────────────────────
 *  LoginPage          → Credential-based auth; Admin can add users
 *  Dashboard          → KPI cards, charts, recent activity
 *  SalesPage          → Record & manage product sales
 *  ExpensePage        → Record & manage operating expenses
 *  InventoryPage      → Track stock levels by product category
 *  TransactionsPage   → Full filterable ledger
 *  ReportsPage        → Monthly summaries, category breakdowns
 *  UsersPage          → Admin-only user management
 *
 *  Tech Stack: React 18, Recharts, Framer Motion, Lucide Icons,
 *              Tailwind CSS (CDN utility classes only)
 * ============================================================
 */

import React, { useState, useMemo } from 'react';
import {
  AreaChart, Area, BarChart, Bar, PieChart, Pie, Cell,
  XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer
} from 'recharts';
import { motion, AnimatePresence } from 'framer-motion';
import {
  LayoutDashboard, TrendingUp, TrendingDown, ShoppingBag,
  FileText, Users, LogOut, Plus, Search, Download, Edit2,
  Trash2, Menu, X, ArrowUpRight, ArrowDownRight, Shield,
  Bell, Lock, Mail, BarChart2, Activity, CheckCircle,
  AlertCircle, Package, DollarSign, ChevronRight, Tag
} from 'lucide-react';

// ─────────────────────────────────────────────────────────────
//  CONSTANTS & UTILITIES
// ─────────────────────────────────────────────────────────────

/** Format a number as Ghanaian Cedis */
const GHS = n =>
  `GH₵${Number(n).toLocaleString('en', {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2
  })}`;

/** Format a date string to a readable format */
const fmtDate = d =>
  d ? new Date(d).toLocaleDateString('en-GB', {
    day: '2-digit', month: 'short', year: 'numeric'
  }) : '';

/** Generate a unique transaction ID */
const uid = () => `DBN${Date.now()}${Math.floor(Math.random() * 1000)}`;

/** Chart colour palette — warm, fashion-forward tones */
const COLORS = [
  '#c9a96e', '#1a1a2e', '#e8b4a0', '#6b4c3b',
  '#d4956a', '#2d4a3e', '#f0c080', '#8b6355'
];

// ── PRODUCT CATEGORIES sold at Daban ─────────────────────────
const PRODUCT_CATS = [
  'Shoes', 'Sneakers', 'Shirts', 'Trousers',
  'Watches', 'Necklaces', 'Bags', 'Accessories', 'Other'
];

// ── EXPENSE CATEGORIES for a retail clothing shop ────────────
const EXPENSE_CATS = [
  'ECG Prepaid',       // electricity
  'Rent',
  'Restocking',        // buying new inventory
  'Staff Wages',
  'Transport',
  'Marketing',
  'Packaging',
  'Equipment',
  'Miscellaneous'
];

/** Role badge colour map */
const ROLE_COLORS = {
  Admin:        'bg-amber-100 text-amber-800 border-amber-200',
  Manager:      'bg-stone-100 text-stone-700 border-stone-200',
  Cashier:      'bg-emerald-100 text-emerald-700 border-emerald-200',
  Auditor:      'bg-blue-100 text-blue-700 border-blue-200',
  Viewer:       'bg-gray-100 text-gray-500 border-gray-200',
};

/** Permission matrix per role */
const PERMS = {
  Admin:   ['view','add','edit','delete','approve','users','reports'],
  Manager: ['view','add','edit','reports'],
  Cashier: ['view','add'],
  Auditor: ['view','reports'],
  Viewer:  ['view'],
};

/** Helper: check if a role has a given permission */
const can = (role, action) => PERMS[role]?.includes(action);


// ─────────────────────────────────────────────────────────────
//  USERS DATABASE  (credentials assigned by Admin)
// ─────────────────────────────────────────────────────────────
const USERS_DB = [
  {
    id: 1,
    name: 'Kobina Praobeng',          // Store owner / admin
    email: 'kobinapraobeng@gmail.com',
    role: 'Admin',
    password: 'admin2026',
    joined: '2024-01-01',
    active: true
  },
  // Additional staff can be added by the Admin from the Users page
];


// ─────────────────────────────────────────────────────────────
//  SEED DATA  — representative transactions for Daban
// ─────────────────────────────────────────────────────────────
const SEED = (() => {
  const txns = [];

  // --- Sales (income) entries ---
  const sales = [
    ['2025-01-04', 'Shoes',       420,  'Walk-in Customer',   'Nike Air Force pair', 'Kobina Praobeng'],
    ['2025-01-10', 'Shirts',      180,  'Instagram Order',    '3x polo shirts',      'Kobina Praobeng'],
    ['2025-01-20', 'Sneakers',    550,  'Walk-in Customer',   'Adidas Originals',    'Kobina Praobeng'],
    ['2025-02-03', 'Watches',     800,  'Referred Customer',  'Luxury quartz watch', 'Kobina Praobeng'],
    ['2025-02-14', 'Necklaces',   350,  'Valentine Promo',    'Gold-plated set',     'Kobina Praobeng'],
    ['2025-02-22', 'Trousers',    240,  'Walk-in Customer',   'Cargo & chinos',      'Kobina Praobeng'],
    ['2025-03-05', 'Sneakers',    620,  'Online Order',       'Jordan 1 Retro',      'Kobina Praobeng'],
    ['2025-03-17', 'Shoes',       390,  'Walk-in Customer',   'Leather loafers',     'Kobina Praobeng'],
    ['2025-03-28', 'Bags',        470,  'Walk-in Customer',   'Crossbody bags ×2',   'Kobina Praobeng'],
    ['2025-04-06', 'Shirts',      320,  'Bulk Order',         '8x t-shirts',         'Kobina Praobeng'],
    ['2025-04-19', 'Watches',     950,  'Referred Customer',  'Chronograph watch',   'Kobina Praobeng'],
    ['2025-05-02', 'Accessories', 210,  'Walk-in Customer',   'Belts & sunglasses',  'Kobina Praobeng'],
    ['2025-05-15', 'Sneakers',    580,  'Instagram Order',    'New Balance 550',     'Kobina Praobeng'],
    ['2025-05-29', 'Trousers',    310,  'Walk-in Customer',   'Denim jeans ×2',      'Kobina Praobeng'],
    ['2025-06-08', 'Shoes',       440,  'Walk-in Customer',   'Oxford shoes',        'Kobina Praobeng'],
    ['2025-06-22', 'Necklaces',   290,  'Online Order',       'Silver chains',       'Kobina Praobeng'],
    ['2025-07-04', 'Bags',        520,  'Walk-in Customer',   'Leather tote bags',   'Kobina Praobeng'],
    ['2025-07-18', 'Shirts',      260,  'Walk-in Customer',   'Button-up shirts',    'Kobina Praobeng'],
    ['2025-08-03', 'Sneakers',    700,  'Bulk Order',         'Wholesale sneakers',  'Kobina Praobeng'],
    ['2025-08-20', 'Watches',     880,  'Walk-in Customer',   'Smart watch',         'Kobina Praobeng'],
    ['2025-09-06', 'Shoes',       460,  'Walk-in Customer',   'Sports shoes ×2',     'Kobina Praobeng'],
    ['2025-09-21', 'Accessories', 330,  'Instagram Order',    'Cap & sunglasses set','Kobina Praobeng'],
    ['2025-10-02', 'Trousers',    280,  'Walk-in Customer',   'Formal trousers',     'Kobina Praobeng'],
    ['2025-10-16', 'Sneakers',    640,  'Online Order',       'Puma Suede Classic',  'Kobina Praobeng'],
  ];

  // --- Expense entries ---
  const expenses = [
    ['2025-01-07',  'ECG Prepaid',  120, 'Electricity top-up January',  'Kobina Praobeng'],
    ['2025-01-15',  'Rent',        1500, 'Monthly shop rent January',    'Kobina Praobeng'],
    ['2025-02-05',  'ECG Prepaid',  150, 'Electricity top-up February',  'Kobina Praobeng'],
    ['2025-02-15',  'Rent',        1500, 'Monthly shop rent February',   'Kobina Praobeng'],
    ['2025-02-20',  'Restocking',   800, 'New sneaker stock from supplier','Kobina Praobeng'],
    ['2025-03-07',  'ECG Prepaid',  130, 'Electricity top-up March',     'Kobina Praobeng'],
    ['2025-03-15',  'Rent',        1500, 'Monthly shop rent March',      'Kobina Praobeng'],
    ['2025-03-25',  'Marketing',    200, 'Instagram ad boost',           'Kobina Praobeng'],
    ['2025-04-05',  'ECG Prepaid',  140, 'Electricity top-up April',     'Kobina Praobeng'],
    ['2025-04-15',  'Rent',        1500, 'Monthly shop rent April',      'Kobina Praobeng'],
    ['2025-04-28',  'Packaging',    180, 'Shopping bags & boxes',        'Kobina Praobeng'],
    ['2025-05-06',  'ECG Prepaid',  125, 'Electricity top-up May',       'Kobina Praobeng'],
    ['2025-05-15',  'Rent',        1500, 'Monthly shop rent May',        'Kobina Praobeng'],
    ['2025-05-22',  'Restocking',  1100, 'Watch & jewellery restock',    'Kobina Praobeng'],
    ['2025-06-05',  'ECG Prepaid',  145, 'Electricity top-up June',      'Kobina Praobeng'],
    ['2025-06-15',  'Rent',        1500, 'Monthly shop rent June',       'Kobina Praobeng'],
    ['2025-07-03',  'ECG Prepaid',  160, 'Electricity top-up July',      'Kobina Praobeng'],
    ['2025-07-15',  'Rent',        1500, 'Monthly shop rent July',       'Kobina Praobeng'],
    ['2025-08-05',  'ECG Prepaid',  135, 'Electricity top-up August',    'Kobina Praobeng'],
    ['2025-08-15',  'Rent',        1500, 'Monthly shop rent August',     'Kobina Praobeng'],
    ['2025-08-25',  'Transport',    250, 'Goods delivery & pickup',      'Kobina Praobeng'],
    ['2025-09-04',  'ECG Prepaid',  128, 'Electricity top-up September', 'Kobina Praobeng'],
    ['2025-09-15',  'Rent',        1500, 'Monthly shop rent September',  'Kobina Praobeng'],
    ['2025-10-03',  'ECG Prepaid',  142, 'Electricity top-up October',   'Kobina Praobeng'],
    ['2025-10-15',  'Rent',        1500, 'Monthly shop rent October',    'Kobina Praobeng'],
  ];

  // Build income transaction objects
  sales.forEach(([date, cat, amount, source, desc, by], i) =>
    txns.push({
      id: `DBN${String(i + 1).padStart(5, '0')}`,
      type: 'income',
      category: cat,
      amount,
      source,
      description: desc,
      recordedBy: by,
      date,
      timestamp: new Date(date).toISOString(),
      editHistory: [],
    })
  );

  // Build expense transaction objects
  expenses.forEach(([date, cat, amount, desc, by], i) =>
    txns.push({
      id: `DBN${String(sales.length + i + 1).padStart(5, '0')}`,
      type: 'expense',
      category: cat,
      amount,
      description: desc,
      paidBy: by,
      date,
      timestamp: new Date(date).toISOString(),
      editHistory: [],
    })
  );

  return txns.sort((a, b) => new Date(a.date) - new Date(b.date));
})();


// ─────────────────────────────────────────────────────────────
//  SHARED UI COMPONENTS
// ─────────────────────────────────────────────────────────────

/** Generic white card container */
const Card = ({ children, className = '' }) => (
  <div className={`bg-white rounded-2xl shadow-sm border border-stone-100 ${className}`}>
    {children}
  </div>
);

/** Pill-shaped badge */
const Badge = ({ label, className = '' }) => (
  <span className={`inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium border ${className}`}>
    {label}
  </span>
);

/** Reusable button with variant styles */
const Btn = ({ children, variant = 'primary', size = 'md', className = '', ...p }) => {
  const v = {
    primary:   'bg-stone-900 hover:bg-stone-800 text-white shadow-sm',
    secondary: 'bg-stone-100 hover:bg-stone-200 text-stone-700',
    danger:    'bg-red-50 hover:bg-red-100 text-red-600',
    outline:   'border border-stone-200 hover:bg-stone-50 text-stone-700',
    gold:      'bg-amber-500 hover:bg-amber-400 text-white shadow-sm',
  };
  const s = { sm: 'px-3 py-1.5 text-xs', md: 'px-4 py-2 text-sm', lg: 'px-6 py-2.5 text-base' };
  return (
    <button
      className={`inline-flex items-center gap-2 font-medium rounded-xl transition-all ${v[variant]} ${s[size]} ${className}`}
      {...p}
    >
      {children}
    </button>
  );
};

/** Labelled text input */
const FInput = ({ label, ...p }) => (
  <div className="space-y-1.5">
    {label && <label className="block text-sm font-medium text-stone-700">{label}</label>}
    <input
      className="w-full px-3 py-2.5 border border-stone-200 rounded-xl bg-stone-50 focus:bg-white focus:outline-none focus:ring-2 focus:ring-amber-400 text-sm transition-colors"
      {...p}
    />
  </div>
);

/** Labelled select dropdown */
const FSelect = ({ label, children, ...p }) => (
  <div className="space-y-1.5">
    {label && <label className="block text-sm font-medium text-stone-700">{label}</label>}
    <select
      className="w-full px-3 py-2.5 border border-stone-200 rounded-xl bg-stone-50 focus:bg-white focus:outline-none focus:ring-2 focus:ring-amber-400 text-sm transition-colors"
      {...p}
    >
      {children}
    </select>
  </div>
);

/** Animated modal dialog */
const Modal = ({ isOpen, onClose, title, children, size = 'md' }) => {
  const w = { sm: 'max-w-sm', md: 'max-w-lg', lg: 'max-w-2xl', xl: 'max-w-4xl' };
  return (
    <AnimatePresence>
      {isOpen && (
        <motion.div
          initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }}
          className="fixed inset-0 bg-black/50 backdrop-blur-sm z-50 flex items-center justify-center p-4"
          onClick={onClose}
        >
          <motion.div
            initial={{ scale: 0.95, opacity: 0 }}
            animate={{ scale: 1, opacity: 1 }}
            exit={{ scale: 0.95, opacity: 0 }}
            transition={{ type: 'spring', damping: 25, stiffness: 300 }}
            className={`bg-white rounded-2xl shadow-2xl w-full ${w[size]} max-h-screen overflow-y-auto`}
            onClick={e => e.stopPropagation()}
          >
            <div className="flex items-center justify-between px-6 py-4 border-b border-stone-100">
              <h2 className="text-base font-semibold text-stone-900">{title}</h2>
              <button onClick={onClose} className="p-1.5 hover:bg-stone-100 rounded-xl transition-colors">
                <X size={16} className="text-stone-500" />
              </button>
            </div>
            <div className="p-6">{children}</div>
          </motion.div>
        </motion.div>
      )}
    </AnimatePresence>
  );
};

/** KPI summary card with icon and trend */
const StatCard = ({ title, value, sub, icon: Icon, iconBg, trend }) => (
  <motion.div whileHover={{ y: -2 }} className="bg-white rounded-2xl p-5 border border-stone-100 shadow-sm">
    <div className="flex items-start justify-between">
      <div>
        <p className="text-xs text-stone-400 font-medium uppercase tracking-wide">{title}</p>
        <p className="text-xl font-bold text-stone-900 mt-1.5 leading-tight">{value}</p>
        {sub && (
          <p className={`text-xs mt-1 ${
            trend === 'up' ? 'text-emerald-600' :
            trend === 'down' ? 'text-red-500' : 'text-stone-400'
          }`}>{sub}</p>
        )}
      </div>
      <div className={`p-3 rounded-xl ${iconBg}`}><Icon size={18} /></div>
    </div>
  </motion.div>
);

/**
 * Export an array-of-arrays to a CSV file download
 * @param {Array[]} rows  - 2D array of values
 * @param {string} filename - download filename
 */
const exportCSV = (rows, filename) => {
  const csv = rows
    .map(r => r.map(c => `"${String(c).replace(/"/g, '""')}"`).join(','))
    .join('\n');
  const a = document.createElement('a');
  a.href = URL.createObjectURL(new Blob([csv], { type: 'text/csv' }));
  a.download = filename;
  a.click();
};


// ─────────────────────────────────────────────────────────────
//  LOGIN PAGE
// ─────────────────────────────────────────────────────────────

/**
 * LoginPage
 * Shows the Daban branded login screen.
 * Validates email + password against USERS_DB.
 * @param {Function} onLogin - called with user object on success
 */
const LoginPage = ({ onLogin }) => {
  const [email,   setEmail]   = useState('');
  const [pass,    setPass]    = useState('');
  const [err,     setErr]     = useState('');
  const [loading, setLoading] = useState(false);

  const submit = e => {
    e.preventDefault();
    setLoading(true);
    setErr('');
    setTimeout(() => {
      const u = USERS_DB.find(u => u.email === email && u.password === pass && u.active);
      if (u) {
        onLogin(u);
      } else {
        setErr('Invalid email or password. Please try again.');
        setLoading(false);
      }
    }, 700);
  };

  return (
    <div className="min-h-screen bg-stone-950 flex items-center justify-center p-4"
         style={{ backgroundImage: 'radial-gradient(ellipse at 30% 20%, #3d2b1f 0%, #1a1a1a 60%, #0d0d0d 100%)' }}>
      <motion.div
        initial={{ y: 24, opacity: 0 }}
        animate={{ y: 0, opacity: 1 }}
        transition={{ duration: 0.5 }}
        className="w-full max-w-md"
      >
        {/* Brand header */}
        <div className="text-center mb-8">
          {/* Daban logo rendered as text — replace with <img> if needed */}
          <div className="w-20 h-20 bg-white rounded-2xl flex items-center justify-center mx-auto mb-4 shadow-xl">
            <span className="text-2xl font-black text-stone-900 tracking-widest">D</span>
          </div>
          <h1 className="text-3xl font-black text-white tracking-widest uppercase">DABAN</h1>
          <p className="text-amber-400 text-sm mt-1 tracking-wider">Clothing & Apparel · Bookkeeping</p>
        </div>

        {/* Login card */}
        <div className="bg-white/5 backdrop-blur-xl rounded-3xl p-8 border border-white/10 shadow-2xl">
          <h2 className="text-white font-semibold mb-6">Sign in to continue</h2>
          <form onSubmit={submit} className="space-y-4">
            {/* Email field */}
            <div>
              <label className="block text-sm font-medium text-stone-300 mb-1.5">Email Address</label>
              <div className="relative">
                <Mail size={15} className="absolute left-3 top-3 text-stone-400" />
                <input
                  type="email" value={email} onChange={e => setEmail(e.target.value)}
                  placeholder="your@email.com" required
                  className="w-full pl-9 pr-4 py-2.5 bg-white/10 border border-white/20 rounded-xl text-white placeholder-stone-500 focus:outline-none focus:ring-2 focus:ring-amber-400 text-sm"
                />
              </div>
            </div>
            {/* Password field */}
            <div>
              <label className="block text-sm font-medium text-stone-300 mb-1.5">Password</label>
              <div className="relative">
                <Lock size={15} className="absolute left-3 top-3 text-stone-400" />
                <input
                  type="password" value={pass} onChange={e => setPass(e.target.value)}
                  placeholder="••••••••" required
                  className="w-full pl-9 pr-4 py-2.5 bg-white/10 border border-white/20 rounded-xl text-white placeholder-stone-500 focus:outline-none focus:ring-2 focus:ring-amber-400 text-sm"
                />
              </div>
            </div>
            {/* Error message */}
            {err && (
              <div className="flex items-center gap-2 bg-red-500/20 border border-red-400/30 rounded-xl px-3 py-2.5">
                <AlertCircle size={14} className="text-red-300 shrink-0" />
                <p className="text-red-300 text-xs">{err}</p>
              </div>
            )}
            {/* Submit button */}
            <button
              type="submit" disabled={loading}
              className="w-full bg-amber-500 hover:bg-amber-400 text-white font-semibold py-3 rounded-xl transition-all mt-1 disabled:opacity-60 text-sm"
            >
              {loading ? 'Signing in…' : 'Sign In →'}
            </button>
          </form>
        </div>

        <p className="text-stone-600 text-xs text-center mt-6">
          © {new Date().getFullYear()} Daban Clothing & Apparel
        </p>
      </motion.div>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  DASHBOARD
// ─────────────────────────────────────────────────────────────

/**
 * Dashboard
 * Displays high-level KPI cards, bar chart (revenue vs expenses),
 * pie chart (expense breakdown), recent transactions, and top-selling categories.
 */
const Dashboard = ({ transactions, user }) => {
  const sales    = transactions.filter(t => t.type === 'income');
  const expenses = transactions.filter(t => t.type === 'expense');

  const totalSales   = sales.reduce((s, t) => s + t.amount, 0);
  const totalExpense = expenses.reduce((s, t) => s + t.amount, 0);
  const balance      = totalSales - totalExpense;

  // Build monthly chart data for 2025
  const months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
  const monthly = months.map((m, i) => {
    const mo  = String(i + 1).padStart(2, '0');
    const inc = sales.filter(t => t.date?.startsWith(`2025-${mo}`)).reduce((s, t) => s + t.amount, 0);
    const exp = expenses.filter(t => t.date?.startsWith(`2025-${mo}`)).reduce((s, t) => s + t.amount, 0);
    return { month: m, revenue: inc, expenses: exp, profit: inc - exp };
  });

  // Expense breakdown by category for donut chart
  const expByCat = EXPENSE_CATS
    .map(c => ({ name: c, value: expenses.filter(t => t.category === c).reduce((s, t) => s + t.amount, 0) }))
    .filter(c => c.value > 0);

  // Top 5 most recent transactions
  const recent = [...transactions]
    .sort((a, b) => new Date(b.date) - new Date(a.date))
    .slice(0, 6);

  // Large expense alert (>= GH₵1000)
  const largeExp = expenses
    .filter(t => t.amount >= 1000)
    .sort((a, b) => new Date(b.date) - new Date(a.date))
    .slice(0, 3);

  return (
    <div className="space-y-6">
      {/* Page heading */}
      <div>
        <h1 className="text-2xl font-bold text-stone-900">
          Welcome back, {user.name.split(' ')[0]} 👋
        </h1>
        <p className="text-stone-400 text-sm mt-1">
          Financial overview — Daban Clothing & Apparel
        </p>
      </div>

      {/* Large expense alert banner */}
      {largeExp.length > 0 && (
        <div className="bg-amber-50 border border-amber-200 rounded-2xl p-4 flex items-start gap-3">
          <Bell size={16} className="text-amber-600 mt-0.5 shrink-0" />
          <div>
            <p className="text-sm font-semibold text-amber-800">Large Expense Alert</p>
            <p className="text-xs text-amber-600 mt-0.5">
              {largeExp.map(t => `${t.description} (${GHS(t.amount)})`).join(' · ')}
            </p>
          </div>
        </div>
      )}

      {/* KPI cards */}
      <div className="grid grid-cols-2 lg:grid-cols-4 gap-4">
        <StatCard
          title="Net Balance"    value={GHS(balance)}
          sub={balance >= 0 ? 'Healthy surplus' : 'Review expenses'}
          icon={DollarSign} iconBg="bg-amber-50 text-amber-600"
          trend={balance >= 0 ? 'up' : 'down'}
        />
        <StatCard
          title="Total Revenue"  value={GHS(totalSales)}
          sub={`${sales.length} sales`}
          icon={TrendingUp} iconBg="bg-emerald-50 text-emerald-600" trend="up"
        />
        <StatCard
          title="Total Expenses" value={GHS(totalExpense)}
          sub={`${expenses.length} entries`}
          icon={TrendingDown} iconBg="bg-red-50 text-red-500" trend="down"
        />
        <StatCard
          title="Products Sold"  value={sales.length}
          sub="All-time transactions"
          icon={ShoppingBag} iconBg="bg-stone-100 text-stone-600"
        />
      </div>

      {/* Charts row */}
      <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
        {/* Revenue vs Expenses bar chart */}
        <Card className="lg:col-span-2 p-6">
          <h3 className="font-semibold text-stone-900 mb-4">Revenue vs Expenses — 2025</h3>
          <ResponsiveContainer width="100%" height={210}>
            <BarChart data={monthly} barSize={14} barGap={3}>
              <CartesianGrid strokeDasharray="3 3" stroke="#f5f5f4" vertical={false} />
              <XAxis dataKey="month" tick={{ fontSize: 11 }} axisLine={false} tickLine={false} />
              <YAxis tick={{ fontSize: 10 }} axisLine={false} tickLine={false}
                tickFormatter={v => `₵${(v / 1000).toFixed(0)}k`} />
              <Tooltip
                formatter={v => GHS(v)}
                contentStyle={{ borderRadius: 12, border: '1px solid #e7e5e4', fontSize: 12 }}
              />
              <Legend iconType="circle" iconSize={8} wrapperStyle={{ fontSize: 12 }} />
              <Bar dataKey="revenue"  fill="#c9a96e" radius={[4,4,0,0]} name="Revenue" />
              <Bar dataKey="expenses" fill="#f87171" radius={[4,4,0,0]} name="Expenses" />
            </BarChart>
          </ResponsiveContainer>
        </Card>

        {/* Expense breakdown donut chart */}
        <Card className="p-6">
          <h3 className="font-semibold text-stone-900 mb-4">Expense Breakdown</h3>
          <ResponsiveContainer width="100%" height={140}>
            <PieChart>
              <Pie data={expByCat} cx="50%" cy="50%" innerRadius={40} outerRadius={65}
                paddingAngle={3} dataKey="value">
                {expByCat.map((_, i) => <Cell key={i} fill={COLORS[i % COLORS.length]} />)}
              </Pie>
              <Tooltip formatter={v => GHS(v)} contentStyle={{ borderRadius: 12, border: '1px solid #e7e5e4', fontSize: 11 }} />
            </PieChart>
          </ResponsiveContainer>
          <div className="space-y-1.5 mt-1 overflow-y-auto max-h-28">
            {expByCat.map((item, i) => (
              <div key={i} className="flex items-center justify-between">
                <div className="flex items-center gap-1.5">
                  <div className="w-2.5 h-2.5 rounded-full shrink-0" style={{ background: COLORS[i % COLORS.length] }} />
                  <span className="text-xs text-stone-500">{item.name}</span>
                </div>
                <span className="text-xs font-semibold text-stone-700">{GHS(item.value)}</span>
              </div>
            ))}
          </div>
        </Card>
      </div>

      {/* Recent transactions */}
      <Card className="p-6">
        <div className="flex items-center justify-between mb-4">
          <h3 className="font-semibold text-stone-900">Recent Transactions</h3>
          <span className="text-xs text-stone-400">{recent.length} records</span>
        </div>
        <div className="space-y-2.5">
          {recent.map(t => (
            <div key={t.id} className="flex items-center justify-between gap-3">
              <div className="flex items-center gap-2.5 min-w-0">
                <div className={`w-7 h-7 rounded-lg flex items-center justify-center shrink-0 ${
                  t.type === 'income' ? 'bg-emerald-50' : 'bg-red-50'
                }`}>
                  {t.type === 'income'
                    ? <ArrowUpRight size={13} className="text-emerald-600" />
                    : <ArrowDownRight size={13} className="text-red-500" />}
                </div>
                <div className="min-w-0">
                  <p className="text-xs font-medium text-stone-800 truncate">{t.description}</p>
                  <p className="text-xs text-stone-400">{t.category} · {fmtDate(t.date)}</p>
                </div>
              </div>
              <span className={`text-xs font-bold shrink-0 ${
                t.type === 'income' ? 'text-emerald-600' : 'text-red-500'
              }`}>
                {t.type === 'income' ? '+' : '-'}{GHS(t.amount)}
              </span>
            </div>
          ))}
        </div>
      </Card>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  SALES PAGE  (Income)
// ─────────────────────────────────────────────────────────────

/**
 * SalesPage
 * Lists all income/sales records.
 * Allows adding, editing, and deleting entries (permission-gated).
 */
const SalesPage = ({ transactions, onAdd, onEdit, onDelete, user }) => {
  const [modal,   setModal]   = useState(false);
  const [editRec, setEditRec] = useState(null);
  const [search,  setSearch]  = useState('');
  const [cat,     setCat]     = useState('');

  // Blank form state
  const blank = {
    amount: '', category: 'Shoes', source: '',
    description: '', recordedBy: user.name,
    date: new Date().toISOString().slice(0, 10)
  };
  const [form, setForm] = useState(blank);

  // Filter to income transactions only
  const sales = transactions.filter(t => t.type === 'income');

  // Apply search and category filter
  const filtered = sales.filter(t => {
    const s = search.toLowerCase();
    return (
      (!s || [t.description, t.source, t.category].some(v => v?.toLowerCase().includes(s))) &&
      (!cat || t.category === cat)
    );
  });

  const total = sales.reduce((s, t) => s + t.amount, 0);

  // Submit add or edit
  const submit = e => {
    e.preventDefault();
    if (editRec) {
      onEdit({ ...editRec, ...form, amount: parseFloat(form.amount) });
    } else {
      onAdd({
        id: uid(), type: 'income', ...form,
        amount: parseFloat(form.amount),
        timestamp: new Date().toISOString(), editHistory: []
      });
    }
    setModal(false); setEditRec(null); setForm(blank);
  };

  // Open edit modal pre-filled with existing record
  const openEdit = t => {
    setEditRec(t);
    setForm({
      amount: t.amount, category: t.category, source: t.source,
      description: t.description, recordedBy: t.recordedBy, date: t.date
    });
    setModal(true);
  };

  return (
    <div className="space-y-6">
      {/* Header */}
      <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
        <div>
          <h1 className="text-2xl font-bold text-stone-900">Sales Records</h1>
          <p className="text-stone-400 text-sm">
            Total Revenue: <span className="text-emerald-600 font-semibold">{GHS(total)}</span>
            {' '}· {sales.length} records
          </p>
        </div>
        <div className="flex gap-2">
          <Btn variant="outline" size="sm" onClick={() => exportCSV(
            [['ID','Date','Category','Source','Description','Amount','Recorded By'],
             ...filtered.map(t => [t.id, t.date, t.category, t.source, t.description, t.amount, t.recordedBy])],
            'daban-sales.csv'
          )}>
            <Download size={14} />CSV
          </Btn>
          {can(user.role, 'add') && (
            <Btn variant="gold" onClick={() => { setEditRec(null); setForm(blank); setModal(true); }}>
              <Plus size={15} />Record Sale
            </Btn>
          )}
        </div>
      </div>

      {/* Filters */}
      <Card className="p-4">
        <div className="flex flex-col sm:flex-row gap-3">
          <div className="relative flex-1">
            <Search size={14} className="absolute left-3 top-3 text-stone-400" />
            <input
              value={search} onChange={e => setSearch(e.target.value)}
              placeholder="Search sales records…"
              className="w-full pl-9 pr-4 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400 focus:bg-white"
            />
          </div>
          <select value={cat} onChange={e => setCat(e.target.value)}
            className="px-3 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400">
            <option value="">All Products</option>
            {PRODUCT_CATS.map(c => <option key={c}>{c}</option>)}
          </select>
        </div>
      </Card>

      {/* Table */}
      <Card>
        <div className="overflow-x-auto">
          <table className="w-full text-sm">
            <thead>
              <tr className="border-b border-stone-100">
                {['ID','Date','Product','Source','Description','Amount','Recorded By',''].map(h => (
                  <th key={h} className="px-4 py-3 text-left text-xs font-semibold text-stone-400 uppercase tracking-wide whitespace-nowrap">{h}</th>
                ))}
              </tr>
            </thead>
            <tbody>
              {filtered.length === 0
                ? <tr><td colSpan={8} className="px-4 py-10 text-center text-stone-400">No sales records found</td></tr>
                : filtered.map(t => (
                  <tr key={t.id} className="border-b border-stone-50 hover:bg-stone-50/50 transition-colors">
                    <td className="px-4 py-3 font-mono text-xs text-stone-400">{t.id}</td>
                    <td className="px-4 py-3 text-stone-600 whitespace-nowrap">{fmtDate(t.date)}</td>
                    <td className="px-4 py-3">
                      <span className="px-2 py-0.5 bg-amber-50 text-amber-700 rounded-lg text-xs font-medium">
                        {t.category}
                      </span>
                    </td>
                    <td className="px-4 py-3 text-stone-700">{t.source}</td>
                    <td className="px-4 py-3 text-stone-700 max-w-xs truncate">{t.description}</td>
                    <td className="px-4 py-3 font-semibold text-emerald-600 whitespace-nowrap">{GHS(t.amount)}</td>
                    <td className="px-4 py-3 text-stone-500">{t.recordedBy}</td>
                    <td className="px-4 py-3">
                      <div className="flex items-center gap-1">
                        {can(user.role, 'edit') && (
                          <button onClick={() => openEdit(t)} className="p-1.5 hover:bg-amber-50 rounded-lg transition-colors">
                            <Edit2 size={13} className="text-amber-500" />
                          </button>
                        )}
                        {can(user.role, 'delete') && (
                          <button onClick={() => onDelete(t.id)} className="p-1.5 hover:bg-red-50 rounded-lg transition-colors">
                            <Trash2 size={13} className="text-red-400" />
                          </button>
                        )}
                      </div>
                    </td>
                  </tr>
                ))}
            </tbody>
          </table>
        </div>
      </Card>

      {/* Add / Edit modal */}
      <Modal isOpen={modal} onClose={() => setModal(false)}
        title={editRec ? 'Edit Sale Record' : 'Record New Sale'}>
        <form onSubmit={submit} className="space-y-4">
          <div className="grid grid-cols-2 gap-4">
            <FInput label="Amount (GH₵)" type="number" min="0.01" step="0.01"
              value={form.amount} onChange={e => setForm({ ...form, amount: e.target.value })} required />
            <FSelect label="Product Category" value={form.category}
              onChange={e => setForm({ ...form, category: e.target.value })}>
              {PRODUCT_CATS.map(c => <option key={c}>{c}</option>)}
            </FSelect>
          </div>
          <FInput label="Source" value={form.source}
            onChange={e => setForm({ ...form, source: e.target.value })}
            placeholder="e.g. Walk-in Customer, Instagram Order" required />
          <FInput label="Description" value={form.description}
            onChange={e => setForm({ ...form, description: e.target.value })}
            placeholder="Brief description of what was sold" required />
          <div className="grid grid-cols-2 gap-4">
            <FInput label="Recorded By" value={form.recordedBy}
              onChange={e => setForm({ ...form, recordedBy: e.target.value })} required />
            <FInput label="Date" type="date" value={form.date}
              onChange={e => setForm({ ...form, date: e.target.value })} required />
          </div>
          <div className="flex gap-3 pt-1">
            <Btn type="submit" variant="gold" className="flex-1 justify-center">
              {editRec ? 'Update Sale' : 'Save Sale'}
            </Btn>
            <Btn type="button" variant="secondary" onClick={() => setModal(false)}>Cancel</Btn>
          </div>
        </form>
      </Modal>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  EXPENSE PAGE
// ─────────────────────────────────────────────────────────────

/**
 * ExpensePage
 * Lists all operating expenses.
 * Includes ECG Prepaid and all other Daban-specific categories.
 */
const ExpensePage = ({ transactions, onAdd, onEdit, onDelete, user }) => {
  const [modal,   setModal]   = useState(false);
  const [editRec, setEditRec] = useState(null);
  const [search,  setSearch]  = useState('');
  const [cat,     setCat]     = useState('');

  const blank = {
    amount: '', category: 'ECG Prepaid', description: '',
    paidBy: user.name, date: new Date().toISOString().slice(0, 10)
  };
  const [form, setForm] = useState(blank);

  const expenses = transactions.filter(t => t.type === 'expense');
  const filtered = expenses.filter(t => {
    const s = search.toLowerCase();
    return (
      (!s || [t.description, t.category].some(v => v?.toLowerCase().includes(s))) &&
      (!cat || t.category === cat)
    );
  });

  const total = expenses.reduce((s, t) => s + t.amount, 0);

  const submit = e => {
    e.preventDefault();
    if (editRec) {
      onEdit({ ...editRec, ...form, amount: parseFloat(form.amount) });
    } else {
      onAdd({
        id: uid(), type: 'expense', ...form,
        amount: parseFloat(form.amount),
        timestamp: new Date().toISOString(), editHistory: []
      });
    }
    setModal(false); setEditRec(null); setForm(blank);
  };

  const openEdit = t => {
    setEditRec(t);
    setForm({ amount: t.amount, category: t.category, description: t.description, paidBy: t.paidBy, date: t.date });
    setModal(true);
  };

  return (
    <div className="space-y-6">
      <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
        <div>
          <h1 className="text-2xl font-bold text-stone-900">Expense Records</h1>
          <p className="text-stone-400 text-sm">
            Total: <span className="text-red-500 font-semibold">{GHS(total)}</span>
            {' '}· {expenses.length} records
          </p>
        </div>
        <div className="flex gap-2">
          <Btn variant="outline" size="sm" onClick={() => exportCSV(
            [['ID','Date','Category','Description','Amount','Paid By'],
             ...filtered.map(t => [t.id, t.date, t.category, t.description, t.amount, t.paidBy])],
            'daban-expenses.csv'
          )}>
            <Download size={14} />CSV
          </Btn>
          {can(user.role, 'add') && (
            <Btn onClick={() => { setEditRec(null); setForm(blank); setModal(true); }}>
              <Plus size={15} />Record Expense
            </Btn>
          )}
        </div>
      </div>

      {/* Filters */}
      <Card className="p-4">
        <div className="flex flex-col sm:flex-row gap-3">
          <div className="relative flex-1">
            <Search size={14} className="absolute left-3 top-3 text-stone-400" />
            <input value={search} onChange={e => setSearch(e.target.value)}
              placeholder="Search expenses…"
              className="w-full pl-9 pr-4 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400 focus:bg-white" />
          </div>
          <select value={cat} onChange={e => setCat(e.target.value)}
            className="px-3 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400">
            <option value="">All Categories</option>
            {EXPENSE_CATS.map(c => <option key={c}>{c}</option>)}
          </select>
        </div>
      </Card>

      {/* Table */}
      <Card>
        <div className="overflow-x-auto">
          <table className="w-full text-sm">
            <thead>
              <tr className="border-b border-stone-100">
                {['ID','Date','Category','Description','Amount','Paid By',''].map(h => (
                  <th key={h} className="px-4 py-3 text-left text-xs font-semibold text-stone-400 uppercase tracking-wide whitespace-nowrap">{h}</th>
                ))}
              </tr>
            </thead>
            <tbody>
              {filtered.length === 0
                ? <tr><td colSpan={7} className="px-4 py-10 text-center text-stone-400">No expenses found</td></tr>
                : filtered.map(t => (
                  <tr key={t.id} className={`border-b border-stone-50 hover:bg-stone-50/50 transition-colors ${t.amount >= 1000 ? 'bg-amber-50/20' : ''}`}>
                    <td className="px-4 py-3 font-mono text-xs text-stone-400">{t.id}</td>
                    <td className="px-4 py-3 text-stone-600 whitespace-nowrap">{fmtDate(t.date)}</td>
                    <td className="px-4 py-3">
                      <span className="px-2 py-0.5 bg-red-50 text-red-600 rounded-lg text-xs font-medium">
                        {t.category}
                      </span>
                    </td>
                    <td className="px-4 py-3 text-stone-700 max-w-xs truncate">{t.description}</td>
                    <td className="px-4 py-3 font-semibold text-red-500 whitespace-nowrap">
                      {t.amount >= 1000 && <AlertCircle size={11} className="inline mr-1 text-amber-500" />}
                      {GHS(t.amount)}
                    </td>
                    <td className="px-4 py-3 text-stone-500">{t.paidBy}</td>
                    <td className="px-4 py-3">
                      <div className="flex items-center gap-1">
                        {can(user.role, 'edit') && (
                          <button onClick={() => openEdit(t)} className="p-1.5 hover:bg-amber-50 rounded-lg transition-colors">
                            <Edit2 size={13} className="text-amber-500" />
                          </button>
                        )}
                        {can(user.role, 'delete') && (
                          <button onClick={() => onDelete(t.id)} className="p-1.5 hover:bg-red-50 rounded-lg transition-colors">
                            <Trash2 size={13} className="text-red-400" />
                          </button>
                        )}
                      </div>
                    </td>
                  </tr>
                ))}
            </tbody>
          </table>
        </div>
      </Card>

      {/* Add / Edit modal */}
      <Modal isOpen={modal} onClose={() => setModal(false)}
        title={editRec ? 'Edit Expense' : 'Record New Expense'}>
        <form onSubmit={submit} className="space-y-4">
          <div className="grid grid-cols-2 gap-4">
            <FInput label="Amount (GH₵)" type="number" min="0.01" step="0.01"
              value={form.amount} onChange={e => setForm({ ...form, amount: e.target.value })} required />
            <FSelect label="Category" value={form.category}
              onChange={e => setForm({ ...form, category: e.target.value })}>
              {EXPENSE_CATS.map(c => <option key={c}>{c}</option>)}
            </FSelect>
          </div>
          <FInput label="Description" value={form.description}
            onChange={e => setForm({ ...form, description: e.target.value })}
            placeholder="What was this expense for?" required />
          <div className="grid grid-cols-2 gap-4">
            <FInput label="Paid By" value={form.paidBy}
              onChange={e => setForm({ ...form, paidBy: e.target.value })} required />
            <FInput label="Date" type="date" value={form.date}
              onChange={e => setForm({ ...form, date: e.target.value })} required />
          </div>
          <div className="flex gap-3 pt-1">
            <Btn type="submit" className="flex-1 justify-center">
              {editRec ? 'Update Expense' : 'Save Expense'}
            </Btn>
            <Btn type="button" variant="secondary" onClick={() => setModal(false)}>Cancel</Btn>
          </div>
        </form>
      </Modal>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  TRANSACTIONS LEDGER
// ─────────────────────────────────────────────────────────────

/**
 * TransactionsPage
 * Full filterable ledger of all income + expense entries.
 * Supports search, type filter, category filter, and date range.
 */
const TransactionsPage = ({ transactions }) => {
  const [search, setSearch] = useState('');
  const [type,   setType]   = useState('');
  const [cat,    setCat]    = useState('');
  const [from,   setFrom]   = useState('');
  const [to,     setTo]     = useState('');

  const filtered = [...transactions]
    .filter(t => {
      const s = search.toLowerCase();
      return (
        (!s || [t.id, t.description, t.category].some(v => v?.toLowerCase().includes(s))) &&
        (!type || t.type === type) &&
        (!cat  || t.category === cat) &&
        (!from || t.date >= from) &&
        (!to   || t.date <= to)
      );
    })
    .sort((a, b) => new Date(b.date) - new Date(a.date));

  const totalInc = filtered.filter(t => t.type === 'income').reduce((s, t) => s + t.amount, 0);
  const totalExp = filtered.filter(t => t.type === 'expense').reduce((s, t) => s + t.amount, 0);

  return (
    <div className="space-y-6">
      <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
        <div>
          <h1 className="text-2xl font-bold text-stone-900">Transaction Ledger</h1>
          <p className="text-stone-400 text-sm">{filtered.length} of {transactions.length} records</p>
        </div>
        <Btn variant="outline" size="sm" onClick={() => exportCSV(
          [['Transaction ID','Type','Category','Description','Amount','Date','Entered By'],
           ...filtered.map(t => [t.id, t.type, t.category, t.description, t.amount, t.date, t.recordedBy || t.paidBy || ''])],
          'daban-ledger.csv'
        )}>
          <Download size={14} />Export CSV
        </Btn>
      </div>

      {/* Filtered totals */}
      <div className="grid grid-cols-3 gap-4">
        <Card className="p-4">
          <p className="text-xs text-stone-400 uppercase tracking-wide">Filtered Revenue</p>
          <p className="text-lg font-bold text-emerald-600 mt-1">{GHS(totalInc)}</p>
        </Card>
        <Card className="p-4">
          <p className="text-xs text-stone-400 uppercase tracking-wide">Filtered Expenses</p>
          <p className="text-lg font-bold text-red-500 mt-1">{GHS(totalExp)}</p>
        </Card>
        <Card className="p-4">
          <p className="text-xs text-stone-400 uppercase tracking-wide">Net</p>
          <p className={`text-lg font-bold mt-1 ${totalInc - totalExp >= 0 ? 'text-amber-600' : 'text-red-500'}`}>
            {GHS(totalInc - totalExp)}
          </p>
        </Card>
      </div>

      {/* Filter bar */}
      <Card className="p-4">
        <div className="grid grid-cols-2 lg:grid-cols-4 gap-3">
          <div className="col-span-2 lg:col-span-1 relative">
            <Search size={14} className="absolute left-3 top-3 text-stone-400" />
            <input value={search} onChange={e => setSearch(e.target.value)} placeholder="Search…"
              className="w-full pl-9 pr-4 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400 focus:bg-white" />
          </div>
          <select value={type} onChange={e => setType(e.target.value)}
            className="px-3 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400">
            <option value="">All Types</option>
            <option value="income">Income</option>
            <option value="expense">Expense</option>
          </select>
          <select value={cat} onChange={e => setCat(e.target.value)}
            className="px-3 py-2.5 border border-stone-200 rounded-xl text-sm bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400">
            <option value="">All Categories</option>
            {[...PRODUCT_CATS, ...EXPENSE_CATS].map(c => <option key={c}>{c}</option>)}
          </select>
          <div className="flex gap-2">
            <input type="date" value={from} onChange={e => setFrom(e.target.value)}
              className="flex-1 px-2 py-2.5 border border-stone-200 rounded-xl text-xs bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400" />
            <input type="date" value={to} onChange={e => setTo(e.target.value)}
              className="flex-1 px-2 py-2.5 border border-stone-200 rounded-xl text-xs bg-stone-50 focus:outline-none focus:ring-2 focus:ring-amber-400" />
          </div>
        </div>
      </Card>

      {/* Ledger table */}
      <Card>
        <div className="overflow-x-auto">
          <table className="w-full text-sm">
            <thead>
              <tr className="border-b border-stone-100">
                {['Transaction ID','Date','Type','Category','Description','Amount','Entered By'].map(h => (
                  <th key={h} className="px-4 py-3 text-left text-xs font-semibold text-stone-400 uppercase tracking-wide whitespace-nowrap">{h}</th>
                ))}
              </tr>
            </thead>
            <tbody>
              {filtered.length === 0
                ? <tr><td colSpan={7} className="px-4 py-10 text-center text-stone-400">No transactions match your filters</td></tr>
                : filtered.map(t => (
                  <tr key={t.id} className="border-b border-stone-50 hover:bg-stone-50/50 transition-colors">
                    <td className="px-4 py-3 font-mono text-xs text-stone-400">{t.id}</td>
                    <td className="px-4 py-3 text-stone-600 whitespace-nowrap">{fmtDate(t.date)}</td>
                    <td className="px-4 py-3">
                      <span className={`inline-flex items-center gap-1 px-2 py-0.5 rounded-lg text-xs font-semibold ${
                        t.type === 'income' ? 'bg-emerald-50 text-emerald-700' : 'bg-red-50 text-red-600'
                      }`}>
                        {t.type === 'income' ? <ArrowUpRight size={11} /> : <ArrowDownRight size={11} />}
                        {t.type}
                      </span>
                    </td>
                    <td className="px-4 py-3 text-stone-600">{t.category}</td>
                    <td className="px-4 py-3 text-stone-700 max-w-xs truncate">{t.description}</td>
                    <td className={`px-4 py-3 font-semibold whitespace-nowrap ${
                      t.type === 'income' ? 'text-emerald-600' : 'text-red-500'
                    }`}>
                      {t.type === 'income' ? '+' : '-'}{GHS(t.amount)}
                    </td>
                    <td className="px-4 py-3 text-stone-500">{t.recordedBy || t.paidBy}</td>
                  </tr>
                ))}
            </tbody>
          </table>
        </div>
      </Card>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  REPORTS PAGE
// ─────────────────────────────────────────────────────────────

/**
 * ReportsPage
 * Annual financial summary: monthly chart, income by product,
 * expense by category, and profit margin.
 */
const ReportsPage = ({ transactions }) => {
  const sales    = transactions.filter(t => t.type === 'income');
  const expenses = transactions.filter(t => t.type === 'expense');
  const totalSales   = sales.reduce((s, t) => s + t.amount, 0);
  const totalExpense = expenses.reduce((s, t) => s + t.amount, 0);
  const bal          = totalSales - totalExpense;
  const margin       = totalSales > 0 ? ((bal / totalSales) * 100).toFixed(1) : 0;

  const months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
  const monthly = months.map((m, i) => {
    const mo  = String(i + 1).padStart(2, '0');
    const inc = sales.filter(t => t.date?.startsWith(`2025-${mo}`)).reduce((s, t) => s + t.amount, 0);
    const exp = expenses.filter(t => t.date?.startsWith(`2025-${mo}`)).reduce((s, t) => s + t.amount, 0);
    return { month: m, revenue: inc, expenses: exp, profit: inc - exp };
  });

  const salesByCat = PRODUCT_CATS
    .map(c => ({ name: c, value: sales.filter(t => t.category === c).reduce((s, t) => s + t.amount, 0), count: sales.filter(t => t.category === c).length }))
    .filter(c => c.value > 0)
    .sort((a, b) => b.value - a.value);

  const expByCat = EXPENSE_CATS
    .map(c => ({ name: c, value: expenses.filter(t => t.category === c).reduce((s, t) => s + t.amount, 0), count: expenses.filter(t => t.category === c).length }))
    .filter(c => c.value > 0)
    .sort((a, b) => b.value - a.value);

  return (
    <div className="space-y-6">
      <div>
        <h1 className="text-2xl font-bold text-stone-900">Financial Reports</h1>
        <p className="text-stone-400 text-sm">2025 Annual Summary — Daban Clothing & Apparel</p>
      </div>

      {/* Summary KPIs */}
      <div className="grid grid-cols-2 lg:grid-cols-4 gap-4">
        {[
          { label: 'Total Revenue',  val: GHS(totalSales),   color: 'text-emerald-600', bg: 'bg-emerald-50' },
          { label: 'Total Expenses', val: GHS(totalExpense), color: 'text-red-500',     bg: 'bg-red-50' },
          { label: 'Net Profit',     val: GHS(bal),          color: bal >= 0 ? 'text-amber-600' : 'text-red-500', bg: 'bg-amber-50' },
          { label: 'Profit Margin',  val: `${margin}%`,      color: 'text-stone-700',   bg: 'bg-stone-50' },
        ].map(s => (
          <Card key={s.label} className={`p-5 ${s.bg}`}>
            <p className="text-xs text-stone-500 font-medium">{s.label}</p>
            <p className={`text-xl font-bold mt-1 ${s.color}`}>{s.val}</p>
          </Card>
        ))}
      </div>

      {/* Monthly chart */}
      <Card className="p-6">
        <div className="flex items-center justify-between mb-4">
          <h3 className="font-semibold text-stone-900">Monthly Revenue vs Expenses 2025</h3>
          <Btn variant="outline" size="sm" onClick={() => exportCSV(
            [['Month','Revenue','Expenses','Profit'], ...monthly.map(m => [m.month, m.revenue, m.expenses, m.profit])],
            'daban-monthly.csv'
          )}>
            <Download size={14} />Export
          </Btn>
        </div>
        <ResponsiveContainer width="100%" height={250}>
          <BarChart data={monthly} barSize={16} barGap={4}>
            <CartesianGrid strokeDasharray="3 3" stroke="#f5f5f4" vertical={false} />
            <XAxis dataKey="month" tick={{ fontSize: 11 }} axisLine={false} tickLine={false} />
            <YAxis tick={{ fontSize: 10 }} axisLine={false} tickLine={false}
              tickFormatter={v => `₵${(v / 1000).toFixed(0)}k`} />
            <Tooltip formatter={v => GHS(v)} contentStyle={{ borderRadius: 12, border: '1px solid #e7e5e4', fontSize: 12 }} />
            <Legend iconType="circle" iconSize={8} wrapperStyle={{ fontSize: 12 }} />
            <Bar dataKey="revenue"  fill="#c9a96e" radius={[4,4,0,0]} name="Revenue" />
            <Bar dataKey="expenses" fill="#f87171" radius={[4,4,0,0]} name="Expenses" />
          </BarChart>
        </ResponsiveContainer>
      </Card>

      {/* Category breakdowns */}
      <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
        {/* Sales by product */}
        <Card className="p-6">
          <div className="flex items-center justify-between mb-4">
            <h3 className="font-semibold text-stone-900">Revenue by Product</h3>
            <Btn variant="outline" size="sm" onClick={() => exportCSV(
              [['Product','Total','Transactions'], ...salesByCat.map(i => [i.name, i.value, i.count])],
              'daban-sales-breakdown.csv'
            )}>
              <Download size={14} />Export
            </Btn>
          </div>
          <div className="space-y-2.5">
            {salesByCat.map((item, i) => (
              <div key={item.name}>
                <div className="flex items-center justify-between text-sm mb-1">
                  <span className="flex items-center gap-2 text-stone-700">
                    <div className="w-2.5 h-2.5 rounded-full shrink-0" style={{ background: COLORS[i % COLORS.length] }} />
                    {item.name} <span className="text-stone-400 text-xs">({item.count})</span>
                  </span>
                  <span className="font-semibold text-emerald-600">{GHS(item.value)}</span>
                </div>
                <div className="h-1.5 bg-stone-100 rounded-full">
                  <div className="h-full rounded-full"
                    style={{ width: `${(item.value / salesByCat[0].value) * 100}%`, background: COLORS[i % COLORS.length] }} />
                </div>
              </div>
            ))}
          </div>
        </Card>

        {/* Expenses by category */}
        <Card className="p-6">
          <div className="flex items-center justify-between mb-4">
            <h3 className="font-semibold text-stone-900">Expenses by Category</h3>
            <Btn variant="outline" size="sm" onClick={() => exportCSV(
              [['Category','Total','Transactions'], ...expByCat.map(i => [i.name, i.value, i.count])],
              'daban-expense-breakdown.csv'
            )}>
              <Download size={14} />Export
            </Btn>
          </div>
          <div className="space-y-2.5">
            {expByCat.map((item, i) => (
              <div key={item.name}>
                <div className="flex items-center justify-between text-sm mb-1">
                  <span className="flex items-center gap-2 text-stone-700">
                    <div className="w-2.5 h-2.5 rounded-full shrink-0" style={{ background: COLORS[i % COLORS.length] }} />
                    {item.name} <span className="text-stone-400 text-xs">({item.count})</span>
                  </span>
                  <span className="font-semibold text-red-500">{GHS(item.value)}</span>
                </div>
                <div className="h-1.5 bg-stone-100 rounded-full">
                  <div className="h-full rounded-full"
                    style={{ width: `${(item.value / expByCat[0].value) * 100}%`, background: COLORS[i % COLORS.length] }} />
                </div>
              </div>
            ))}
          </div>
        </Card>
      </div>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  USERS PAGE  (Admin only)
// ─────────────────────────────────────────────────────────────

/**
 * UsersPage
 * Admin-only page to view, add, and toggle user accounts.
 * Staff credentials are set here by the Admin.
 */
const UsersPage = ({ users, currentUser, onAddUser, onToggleUser }) => {
  const [modal, setModal] = useState(false);
  const blank = { name: '', email: '', role: 'Cashier', password: '' };
  const [form, setForm] = useState(blank);

  // Restrict access to Admin only
  if (!can(currentUser.role, 'users')) {
    return (
      <div className="flex flex-col items-center justify-center h-64 gap-3">
        <div className="w-14 h-14 bg-stone-100 rounded-2xl flex items-center justify-center">
          <Shield size={28} className="text-stone-400" />
        </div>
        <h3 className="font-semibold text-stone-700">Access Restricted</h3>
        <p className="text-sm text-stone-400 text-center max-w-sm">
          You need Admin privileges to manage users.
        </p>
      </div>
    );
  }

  const submit = e => {
    e.preventDefault();
    onAddUser({
      id: Date.now(), ...form,
      joined: new Date().toISOString().slice(0, 10),
      active: true
    });
    setModal(false); setForm(blank);
  };

  return (
    <div className="space-y-6">
      <div className="flex items-center justify-between">
        <div>
          <h1 className="text-2xl font-bold text-stone-900">User Management</h1>
          <p className="text-stone-400 text-sm">{users.length} registered user{users.length !== 1 ? 's' : ''}</p>
        </div>
        <Btn variant="gold" onClick={() => setModal(true)}>
          <Plus size={15} />Add Staff
        </Btn>
      </div>

      {/* User cards grid */}
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        {users.map(u => (
          <motion.div key={u.id} whileHover={{ y: -2 }}>
            <Card className="p-5">
              <div className="flex items-start justify-between">
                <div className="flex items-center gap-3">
                  {/* Avatar initials */}
                  <div className="w-10 h-10 bg-gradient-to-br from-stone-800 to-amber-600 rounded-xl flex items-center justify-center shrink-0">
                    <span className="text-white font-bold text-sm">
                      {u.name.split(' ').map(n => n[0]).join('').slice(0, 2)}
                    </span>
                  </div>
                  <div>
                    <p className="font-semibold text-stone-900 text-sm">{u.name}</p>
                    <p className="text-xs text-stone-400 truncate max-w-xs">{u.email}</p>
                  </div>
                </div>
                {/* Active / Inactive toggle — cannot toggle self */}
                {currentUser.id !== u.id && (
                  <button onClick={() => onToggleUser(u.id)}
                    className={`px-2 py-1 rounded-lg text-xs font-semibold transition-colors ${
                      u.active
                        ? 'bg-emerald-50 text-emerald-600 hover:bg-emerald-100'
                        : 'bg-stone-100 text-stone-500 hover:bg-stone-200'
                    }`}>
                    {u.active ? 'Active' : 'Inactive'}
                  </button>
                )}
              </div>
              <div className="mt-3 pt-3 border-t border-stone-100 flex items-center justify-between">
                <Badge label={u.role} className={ROLE_COLORS[u.role] || 'bg-stone-100 text-stone-500 border-stone-200'} />
                <span className="text-xs text-stone-400">Since {fmtDate(u.joined)}</span>
              </div>
            </Card>
          </motion.div>
        ))}
      </div>

      {/* Permissions matrix */}
      <Card className="p-5">
        <h3 className="font-semibold text-stone-900 mb-3">Role Permissions</h3>
        <div className="overflow-x-auto">
          <table className="w-full text-sm">
            <thead>
              <tr className="border-b border-stone-100">
                {['Role','View','Add/Edit','Delete','Approve','Users','Reports'].map(h => (
                  <th key={h} className="px-3 py-2 text-left text-xs font-semibold text-stone-400 whitespace-nowrap">{h}</th>
                ))}
              </tr>
            </thead>
            <tbody>
              {Object.entries(PERMS).map(([role, perms]) => (
                <tr key={role} className="border-b border-stone-50">
                  <td className="px-3 py-2.5">
                    <Badge label={role} className={ROLE_COLORS[role] || 'bg-stone-100 text-stone-500 border-stone-200'} />
                  </td>
                  {['view','add','delete','approve','users','reports'].map(p => (
                    <td key={p} className="px-3 py-2.5">
                      {perms.includes(p) || (perms.includes('edit') && p === 'add')
                        ? <CheckCircle size={15} className="text-emerald-500" />
                        : <X size={15} className="text-stone-300" />}
                    </td>
                  ))}
                </tr>
              ))}
            </tbody>
          </table>
        </div>
      </Card>

      {/* Add user modal */}
      <Modal isOpen={modal} onClose={() => setModal(false)} title="Add New Staff Member">
        <form onSubmit={submit} className="space-y-4">
          <FInput label="Full Name" value={form.name}
            onChange={e => setForm({ ...form, name: e.target.value })}
            placeholder="Staff full name" required />
          <FInput label="Email Address" type="email" value={form.email}
            onChange={e => setForm({ ...form, email: e.target.value })}
            placeholder="staff@example.com" required />
          <FSelect label="Role" value={form.role}
            onChange={e => setForm({ ...form, role: e.target.value })}>
            {Object.keys(ROLE_COLORS).map(r => <option key={r}>{r}</option>)}
          </FSelect>
          <FInput label="Password" type="password" value={form.password}
            onChange={e => setForm({ ...form, password: e.target.value })}
            placeholder="Assign a secure password" required />
          <div className="flex gap-3 pt-1">
            <Btn type="submit" variant="gold" className="flex-1 justify-center">Create Account</Btn>
            <Btn type="button" variant="secondary" onClick={() => setModal(false)}>Cancel</Btn>
          </div>
        </form>
      </Modal>
    </div>
  );
};


// ─────────────────────────────────────────────────────────────
//  NAVIGATION CONFIG
// ─────────────────────────────────────────────────────────────

const NAV = [
  { id: 'dashboard',    label: 'Dashboard',    icon: LayoutDashboard },
  { id: 'sales',        label: 'Sales',        icon: TrendingUp },
  { id: 'expenses',     label: 'Expenses',     icon: TrendingDown },
  { id: 'transactions', label: 'Ledger',       icon: FileText },
  { id: 'reports',      label: 'Reports',      icon: Activity },
  { id: 'users',        label: 'Users',        icon: Users },
];


// ─────────────────────────────────────────────────────────────
//  ROOT APPLICATION
// ─────────────────────────────────────────────────────────────

/**
 * App
 * Root component. Manages authentication state, transactions state,
 * users state, and current page routing.
 */
export default function App() {
  // ── State ──────────────────────────────────────────────────
  const [user,    setUser]    = useState(null);          // logged-in user
  const [page,    setPage]    = useState('dashboard');   // current page id
  const [txns,    setTxns]    = useState(SEED);          // all transactions
  const [users,   setUsers]   = useState(USERS_DB);      // registered users
  const [sidebar, setSidebar] = useState(false);         // mobile sidebar open?

  // Show login screen if not authenticated
  if (!user) {
    return <LoginPage onLogin={u => { setUser(u); setPage('dashboard'); }} />;
  }

  // ── CRUD helpers ───────────────────────────────────────────
  /** Add a new transaction */
  const addTxn  = t  => setTxns(p => [...p, t]);
  /** Update an existing transaction by id */
  const editTxn = t  => setTxns(p => p.map(x => x.id === t.id ? t : x));
  /** Delete a transaction by id */
  const delTxn  = id => setTxns(p => p.filter(t => t.id !== id));

  // Shared props passed to page components
  const sharedProps = {
    transactions: txns,
    user,
    onAdd:    addTxn,
    onEdit:   editTxn,
    onDelete: delTxn,
  };

  // ── Page map ───────────────────────────────────────────────
  const pages = {
    dashboard:    <Dashboard    {...sharedProps} />,
    sales:        <SalesPage    {...sharedProps} />,
    expenses:     <ExpensePage  {...sharedProps} />,
    transactions: <TransactionsPage transactions={txns} user={user} />,
    reports:      <ReportsPage  transactions={txns} />,
    users: (
      <UsersPage
        users={users}
        currentUser={user}
        onAddUser={u  => setUsers(p => [...p, u])}
        onToggleUser={id => setUsers(p => p.map(u => u.id === id ? { ...u, active: !u.active } : u))}
      />
    ),
  };

  return (
    <div className="flex h-screen bg-stone-50 overflow-hidden">

      {/* ── Mobile sidebar backdrop ─────────────────────────── */}
      {sidebar && (
        <div className="fixed inset-0 bg-black/40 z-20 lg:hidden"
          onClick={() => setSidebar(false)} />
      )}

      {/* ── Sidebar navigation ──────────────────────────────── */}
      <aside className={`
        fixed lg:static inset-y-0 left-0 z-30 w-60
        bg-stone-950 flex flex-col shadow-xl
        transform transition-transform duration-300
        ${sidebar ? 'translate-x-0' : '-translate-x-full lg:translate-x-0'}
      `}>
        {/* Brand logo */}
        <div className="p-5 border-b border-white/10">
          <div className="flex items-center gap-3">
            <div className="w-9 h-9 bg-amber-500 rounded-xl flex items-center justify-center shrink-0">
              <span className="text-white font-black text-sm tracking-widest">D</span>
            </div>
            <div>
              <p className="font-black text-white text-sm tracking-widest uppercase leading-tight">DABAN</p>
              <p className="text-xs text-stone-400">Clothing & Apparel</p>
            </div>
          </div>
        </div>

        {/* Nav links */}
        <nav className="flex-1 p-3 space-y-0.5 overflow-y-auto">
          {NAV.map(({ id, label, icon: Icon }) => (
            <button key={id}
              onClick={() => { setPage(id); setSidebar(false); }}
              className={`w-full flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium transition-all ${
                page === id
                  ? 'bg-amber-500 text-white shadow-sm'
                  : 'text-stone-400 hover:bg-white/10 hover:text-white'
              }`}>
              <Icon size={17} />{label}
            </button>
          ))}
        </nav>

        {/* User info & logout */}
        <div className="p-4 border-t border-white/10">
          <div className="flex items-center gap-2.5 mb-3">
            <div className="w-8 h-8 bg-gradient-to-br from-stone-600 to-amber-500 rounded-lg flex items-center justify-center shrink-0">
              <span className="text-white text-xs font-bold">
                {user.name.split(' ').map(n => n[0]).join('').slice(0, 2)}
              </span>
            </div>
            <div className="min-w-0">
              <p className="text-xs font-semibold text-white truncate">{user.name}</p>
              <Badge label={user.role} className={`${ROLE_COLORS[user.role]} text-xs`} />
            </div>
          </div>
          <button
            onClick={() => { setUser(null); setPage('dashboard'); }}
            className="w-full flex items-center gap-2 px-3 py-2 text-xs text-stone-500 hover:bg-red-900/30 hover:text-red-400 rounded-xl transition-colors font-medium"
          >
            <LogOut size={14} />Sign Out
          </button>
        </div>
      </aside>

      {/* ── Main content area ────────────────────────────────── */}
      <main className="flex-1 flex flex-col min-w-0 overflow-hidden">
        {/* Mobile top bar */}
        <header className="lg:hidden bg-white border-b border-stone-100 px-4 py-3 flex items-center gap-3">
          <button onClick={() => setSidebar(true)} className="p-1.5 hover:bg-stone-100 rounded-xl">
            <Menu size={20} className="text-stone-600" />
          </button>
          <div className="flex items-center gap-2">
            <div className="w-6 h-6 bg-amber-500 rounded-lg flex items-center justify-center">
              <span className="text-white text-xs font-black">D</span>
            </div>
            <span className="font-semibold text-stone-900 text-sm">
              {NAV.find(n => n.id === page)?.label}
            </span>
          </div>
        </header>

        {/* Page content with enter/exit animation */}
        <div className="flex-1 overflow-y-auto p-5 lg:p-7">
          <AnimatePresence mode="wait">
            <motion.div
              key={page}
              initial={{ opacity: 0, y: 8 }}
              animate={{ opacity: 1, y: 0 }}
              exit={{ opacity: 0, y: -8 }}
              transition={{ duration: 0.18 }}
            >
              {pages[page]}
            </motion.div>
          </AnimatePresence>
        </div>
      </main>
    </div>
  );
}
