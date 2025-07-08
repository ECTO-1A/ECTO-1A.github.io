# Cybersecurity Hardware Page - Quick Add Instructions

## How to Add a New Hardware Item

### Step 1: Upload Your Image
1. Save your hardware image to `/assets/images/hardware/`
2. Use descriptive filenames like `flipper-zero.jpg`, `wifi-pineapple.jpg`, etc.
3. Recommended image size: 400x300px or similar aspect ratio
4. Supported formats: JPG, PNG, WebP

### Step 2: Add the Hardware Item
Copy this template and paste it into the appropriate category section:

```html
<div class="hardware-item">
    <div class="hardware-image">
        <img src="/assets/images/hardware/YOUR_IMAGE.jpg" alt="Device Name" />
    </div>
    <div class="hardware-info">
        <h3 class="hardware-title">Device Name</h3>
        <div class="hardware-description">
            <p>Detailed description of the device, its capabilities, use cases, and any special features. Be descriptive but concise.</p>
        </div>
        <div class="hardware-links">
            <a href="PURCHASE_URL" target="_blank" class="buy-link">
                <i class="fas fa-shopping-cart"></i>
                Buy Here
            </a>
            <!-- Optional: Add multiple purchase links -->
            <a href="ALTERNATIVE_URL" target="_blank" class="buy-link secondary">
                <i class="fas fa-external-link-alt"></i>
                Alternative
            </a>
        </div>
    </div>
</div>
```

### Step 3: Replace the Placeholders
- `YOUR_IMAGE.jpg` → Your actual image filename
- `Device Name` → The name of your hardware
- `Detailed description...` → Your description
- `PURCHASE_URL` → Where to buy the item
- `Buy Here` → Link text (e.g., "Amazon", "Official Store")

### Categories Available:
1. **RF & Wireless Tools** - WiFi, Bluetooth, RF devices
2. **Network Analysis Tools** - Network sniffers, analyzers
3. **Physical Security Tools** - Lock picks, RFID tools
4. **USB & Storage Devices** - USB tools, storage devices
5. **Electronics & Components** - Boards, chips, components
6. **DIY Kits & Build Components** - Build-your-own kits

### Multiple Purchase Links:
You can add multiple purchase options:

```html
<div class="hardware-links">
    <a href="AMAZON_URL" target="_blank" class="buy-link">
        <i class="fas fa-shopping-cart"></i>
        Amazon
    </a>
    <a href="OFFICIAL_URL" target="_blank" class="buy-link secondary">
        <i class="fas fa-external-link-alt"></i>
        Official Store
    </a>
    <a href="ALIEXPRESS_URL" target="_blank" class="buy-link secondary">
        <i class="fas fa-external-link-alt"></i>
        AliExpress
    </a>
</div>
```

### Tips:
- Add items to the most appropriate category
- Use high-quality images for better presentation
- Keep descriptions informative but not too long
- Include key specifications or features
- Test all purchase links before adding
- The first link uses primary styling (red), additional links use secondary styling (gray)

### Image Guidelines:
- Square or landscape orientation works best
- Clear, well-lit photos
- Show the device clearly
- Avoid cluttered backgrounds
- Consistent lighting across all images
