# Merry Christmas!

If you’ve had Santa photos taken by **Scene To Believe** and want to access the full, high-resolution, watermark-free images, follow these simple steps.

### Step 1

Browse to the page that they gave you, ensure that you can see all of your watermarked low resolution images.

### Step 2

Press F12 on your keyboard to open developer tools and click on the **console** tab

### Step 3

Copy the script below and paste it into the console and press **Enter**

```
if (typeof images !== 'undefined') {
    const highResImages = images.filter(img => img.hirescdn);
    if (highResImages.length > 0) {
        const container = document.createElement('div');
        container.innerHTML = `<h3>Download Your High Resolution Images! (${highResImages.length})</h3>`;
        container.style.cssText = 'position: fixed; top: 20px; right: 20px; width: 300px; max-height: 80vh; overflow-y: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 8px 32px rgba(0,0,0,0.3); z-index: 9999;';
        highResImages.forEach(img => {
            const link = document.createElement('a');
            link.href = img.hirescdn;
            link.innerHTML = img.filename;
            link.target = '_blank';
            link.style.cssText = 'display: block; margin: 8px 0; padding: 8px; background: #3498db; color: white; text-decoration: none; border-radius: 6px; text-align: center;';
            container.appendChild(link);
        });
        document.body.appendChild(container);
    }
}
```

If prompted to allow pasting, type in ```allow pasting``` and repeat the above.

### Step 4

Click the links that appear in the top right of the page to download your images!

**Mission Complete!**

## Had a different photo company or the script didn't work? Try this one!

```if (typeof images !== 'undefined') {
    const highResImages = images.filter(img => img.hirescdn);
   
    if (highResImages.length > 0) {
        const container = document.createElement('div');
        container.innerHTML = `
            <div style="text-align: center; margin-bottom: 15px;">
                <h3>Download Your High Resolution Images!</h3>
                <div style="font-size: 14px; color: #666; margin-bottom: 10px;">
                    ${highResImages.length} images available
                </div>
            </div>
        `;
        
        container.style.cssText = `
            position: fixed; 
            top: 20px; 
            right: 20px; 
            width: 320px; 
            max-height: 80vh; 
            overflow-y: auto; 
            background: white; 
            padding: 20px; 
            border-radius: 12px; 
            box-shadow: 0 8px 32px rgba(0,0,0,0.25); 
            z-index: 9999;
            font-family: -apple-system, BlinkMacSystemFont, sans-serif;
        `;
       
        highResImages.forEach(img => {
            const link = document.createElement('a');
            link.href = img.hirescdn;
            link.innerHTML = img.filename;
            link.target = '_blank';
            link.style.cssText = `
                display: block; 
                margin: 8px 0; 
                padding: 12px 10px; 
                background: #3498db; 
                color: white; 
                text-decoration: none; 
                border-radius: 8px; 
                text-align: center;
                font-size: 13px;
                transition: background-color 0.2s;
            `;
            
            link.addEventListener('mouseenter', function() {
                this.style.background = '#2980b9';
            });
            link.addEventListener('mouseleave', function() {
                this.style.background = '#3498db';
            });
            
            container.appendChild(link);
        });
       
        const closeButton = document.createElement('button');
        closeButton.innerHTML = '×';
        closeButton.style.cssText = `
            position: absolute;
            top: 10px;
            right: 15px;
            width: 25px;
            height: 25px;
            border: none;
            background: #e74c3c;
            color: white;
            border-radius: 50%;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            line-height: 1;
        `;
        closeButton.onclick = function() {
            container.remove();
        };
        container.appendChild(closeButton);
       
        document.body.appendChild(container);
        console.log(`High-resolution image panel created with ${highResImages.length} images.`);
    } else {
        console.log('No high-resolution images found.');
    }
} else {
    console.log('Images array not found. Please ensure the page has fully loaded before running this script.');
}```
