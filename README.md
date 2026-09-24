# Rukmini Sarees — Official Website & Product Catalog

A luxury, responsive South Indian ethnic wear catalog website for **Rukmini Sarees**, located in Prasadampadu, Vijayawada. Built with clean vanilla web technologies, dynamic Google Sheets inventory synchronization, and one-click WhatsApp order inquiry routing.

---

## 📍 Store Information

* **Store Name:** Rukmini Sarees
* **Address:** Near Kasturibhai School, Prasadampadu, Vijayawada - 521108, Andhra Pradesh
* **Phone / Call:** [+91 79816 88516](tel:+917981688516)
* **WhatsApp:** [+91 79816 88516](https://wa.me/917981688516)
* **Store Timings:**
  * Monday – Saturday: 10:00 AM – 9:00 PM
  * Sunday: 11:00 AM – 8:00 PM

---

## 📁 Project Structure

```text
rukmini_sarees_final_website/
├── index.html              # Homepage with hero slider, featured edit & category showcase
├── sarees.html             # Pattu & Silk Sarees collection page
├── dress-materials.html    # Unstitched Salwar & Dress Materials collection page
├── dresses.html            # Ready-to-wear Dresses, Kurtis & Nighties page
├── matching.html           # Blouse, Lining, 2M/3M Cloth & Matching Essentials page
├── about.html              # Heritage, weaving tradition & Prasadampadu store story
├── contact.html            # Store location, interactive directions & FAQs
├── README.md               # Complete project documentation & inventory guide
├── css/
│   └── style.css           # Luxury South Indian theme (Temple Red & Royal Gold)
├── js/
│   ├── config.js           # Global store settings & Google Sheet configuration
│   ├── products.js         # Product catalog renderer & Google Sheets live fetcher
│   └── main.js             # Mobile navigation, modal interactions & hero animations
└── data/
    └── products.json       # Built-in offline fallback product catalog
```

---

## 📊 Google Sheets Live Inventory Integration

The website automatically fetches and renders products directly from a live Google Spreadsheet. This allows store managers to update stock, add new items, and adjust prices without touching any code.

### 1. Configuration File
Located at [`js/config.js`](file:///e:/Praveen/rukmini_sarees_final_website/js/config.js):
```javascript
const RUKMINI_CONFIG = {
  storeName: "Rukmini Sarees",
  phone: "+91 79816 88516",
  whatsappNumber: "917981688516",
  address: "Near Kasturibhai School, Prasadampadu, Vijayawada - 521108",
  timings: "Mon – Sat: 10:00 AM – 9:00 PM | Sun: 11:00 AM – 8:00 PM",

  // Live Google Sheet Settings
  googleSheetId: "1PWkCtYvNIRbL9ddKv5CuuX5UC2U1f6b4HXiA4EeMOCs",
  sheetTabName: "Products", // Tab name in the spreadsheet
  cacheExpiryMinutes: 10,   // In-browser cache duration
  fallbackDataUrl: "data/products.json"
};
```

### 2. Google Sheet Column Schema
In your Google Sheet (Tab: **`Products`**), ensure Row 1 has the exact following headers:

| Column # | Header Name | Format / Example | Description |
|:---:|---|---|---|
| **A** | `Product_ID` | `RS-PAT-001` | Unique SKU or code |
| **B** | `Category` | `sarees` | Valid categories: `sarees`, `dress-materials`, `dresses`, `matching` |
| **C** | `Subcategory` | `Bridal Pattu` | Category filter tag (e.g. *Soft Silk*, *Banarasi*, *Chiffon*) |
| **D** | `Product_Name` | `Kanchipuram Crimson Royal Pattu` | **Required**. (Empty names will be skipped) |
| **E** | `Price` | `₹14,500` or `14500` | Selling price displayed on the card |
| **F** | `Original_Price` | `₹18,000` | Optional strikethrough MRP/original price |
| **G** | `Fabric` | `Pure Mulberry Silk with Gold Zari` | Material details shown in quick-view modal |
| **H** | `Color` | `Crimson Red & Antique Gold` | Color palette |
| **I** | `Badge` | `BRIDAL BESTSELLER` | Optional card badge (e.g. *NEW ARRIVAL*, *FESTIVE*) |
| **J** | `Image_URL` | `https://example.com/saree.jpg` | Direct image link |
| **K** | `Description` | `Traditional temple border weave...` | Full description shown in details modal |
| **L** | `In_Stock` | `YES` | Set `YES` to display, or `NO` to hide when sold out |
| **M** | `Featured_Home` | `YES` | Set `YES` to showcase on the homepage featured section |

### 3. How Changes Go Live
1. Add or edit rows in the Google Sheet.
2. In the browser, the data is cached for **10 minutes** (`cacheExpiryMinutes`) to ensure lightning-fast page loading.
3. To view changes immediately, perform a hard refresh (**Ctrl + Shift + R** on Windows or **Cmd + Shift + R** on Mac).
4. If the Google Sheet is inaccessible or contains 0 valid products, the website smoothly falls back to [`data/products.json`](file:///e:/Praveen/rukmini_sarees_final_website/data/products.json).

---

## 💬 WhatsApp Order & Inquiry Flow

Every product card and detail modal includes a direct **WhatsApp Inquiry** button. When clicked:
* Automatically opens WhatsApp directed to `+91 79816 88516`.
* Pre-populates the customer's message with:
  * Product Name
  * Product ID
  * Price
  * Customer intent to inquire / purchase.

---

## 🚀 Deployment

The site is built with pure web standards (zero build step or npm compile required):
1. **GitHub Pages / Netlify / Vercel**: Connect the repository and set publish directory to root (`/`).
2. **cPanel / Traditional Shared Hosting**: Upload all files to your `public_html` directory.
3. **Local Testing**:
   * Open `index.html` via Live Server in VS Code / Antigravity IDE, or:
   ```bash
   npx serve .
   ```
   * Or with Python:
   ```bash
   python -m http.server 8000
   ```

---

## 🎨 Design System

* **Primary Royal Crimson:** `#800020` / `#9b111e`
* **Temple Gold:** `#c5a059` / `#d4af37`
* **Deep Charcoal:** `#1a1a1a`
* **Background Warm Cream:** `#fcfaf7`
* **Typography:**
  * Headings: *Playfair Display* / *Cinzel* (Editorial Serif)
  * Body: *Plus Jakarta Sans* / *Outfit* (Modern Sans-Serif)
