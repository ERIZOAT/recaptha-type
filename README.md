
# How to Identify the Version of reCAPTCHA

When working with reCAPTCHA, it's crucial to identify the version you're dealing with to ensure you implement the right solution. In this guide, we'll explore several methods to help you identify the reCAPTCHA version, including using the CapSolver Extension and recognizing specific patterns.

## 🚀 Method #1 (BEST METHOD): Use CapSolver Extension

Using the CapSolver Extension is the most straightforward and reliable method to identify any CAPTCHA version. It automates the detection process, saving you time and reducing errors.

> For more information on how to use the CapSolver Extension, please visit [CapSolver Blog](https://www.capsolver.com/blog/Extension/identify-any-captcha-and-parameters).

## 🔍 Method #2: Identify the Patterns

If you're unable to use the CapSolver Extension, you can identify the version manually by recognizing specific patterns. Let's break down how to identify the different versions of reCAPTCHA.

### 🍁 Identifying reCAPTCHA V2

**Key Indicators**:

- **Challenge Box:** A challenge box will **always** be present, requiring you to solve a visual puzzle by clicking on images.
  
  ![Example](https://assets.capsolver.com/prod/images/post/2023-09-19/a33066b3-abb4-45a6-9b38-748b69d3c08d.png)
  
- **Domains:** The captcha is typically loaded from either `google.com` or `recaptcha.net`.

### 🌻 Identifying reCAPTCHA V2 Enterprise

**Key Indicators**:

- **Challenge Box:** Like reCAPTCHA V2, a challenge box will **always** be present.
  
  ![Example](https://assets.capsolver.com/prod/images/post/2023-09-19/a33066b3-abb4-45a6-9b38-748b69d3c08d.png)
  
- **Extra Parameters:** The CAPTCHA may include an extra data parameter named `'s'`. This is a unique feature of the Enterprise version.
  
- **Domains:** Like V2, it loads from `google.com` or `recaptcha.net`.
  
- **URL Pattern:** The URL will contain `/enterprise/`, distinguishing it from the standard V2.
  
  **Example URL**: `https://www.google.com/recaptcha/enterprise/anchor`

## 🌟 Identifying reCAPTCHA V2 Invisible

### **Key Indicators**:

- **Challenge Box:** A challenge box **will not always appear** and is triggered only by suspicious activity.
  
  ![Example](https://assets.capsolver.com/prod/images/post/2023-09-19/a33066b3-abb4-45a6-9b38-748b69d3c08d.png)
  
- **Domains:** The captcha is loaded from either `google.com` or `recaptcha.net`.
  
- **No "I'm not a robot" Button:** Instead of the "I'm not a robot" button, an icon will appear in the corner.

### **Using Charles Proxy for Detection**

For a more in-depth analysis, Charles Proxy is a valuable tool. Follow these steps:

1. **Set up Charles:** Download and install [Charles Proxy](https://www.charlesproxy.com/download/).
2. **Enable SSL Proxying:** Navigate to `Proxy > SSL Proxying` and enable SSL Proxying.
  
    ![Charles SSL Proxying](https://assets.capsolver.com/prod/images/post/2023-09-19/a40c902e-3c5c-4f92-b804-0e534fe1d3d3.png)
  
3. **Add Hosts:** Add the following hosts and ports:
   ```plaintext
   Host: www.recaptcha.net, Port: 443
   Host: google.com, Port: 443
   ```

#### **Detection Process in Charles**:

- **Step 1:** Open Charles and navigate to the site with reCAPTCHA.
- **Step 2:** A request from `google.com` or `recaptcha.net` will appear. Click and search for "recaptcha." Reload the request if necessary.

  ![Charles Request](https://assets.capsolver.com/prod/images/post/2023-09-19/159a94b5-4e15-493d-851e-16e4780dc3ff.png)

- **Step 3:** Inspect the `protobuf` at position 6 for a value labeled `'fi'`. This confirms the presence of reCAPTCHA V2 Invisible.
  
  ![Value confirming reCaptcha V2 Invisible](https://assets.capsolver.com/prod/images/post/2023-09-19/2864b8df-57bf-4f1f-bf0a-6bb6069664ef.png)

## 🍀 Identifying reCAPTCHA V3 and V3 Enterprise

### **Key Indicators**:

- **No Challenge Box:** Unlike V2, the challenge box **will not** appear.
- **Domains:** The captcha is loaded from `google.com` or `recaptcha.net`.
- **Icon in Corner:** Instead of the "I'm not a robot" button, an icon appears in the corner.

### **Using Charles Proxy for Detection**

#### **Detection Process in Charles**:

- **Step 1:** With Charles configured, navigate to the site with reCAPTCHA.
- **Step 2:** A request from `google.com` or `recaptcha.net` will appear. Click and search for "recaptcha." Reload the request if necessary.
  
  ![Charles Request](https://assets.capsolver.com/prod/images/post/2023-09-19/159a94b5-4e15-493d-851e-16e4780dc3ff.png)

- **Step 3:** Inspect the `protobuf` at position 8 for a value indicating the `pageAction`. This value confirms the presence of reCAPTCHA V3 or V3 Enterprise.
  
  ![Value confirming reCaptcha V3](https://assets.capsolver.com/prod/images/post/2023-09-19/c41cc85c-5739-41e2-aba4-7f633ff757bd.png)

## 👀 Additional Resources

If you’re looking to dive deeper into solving reCAPTCHA challenges, check out these additional resources:

- **[How to Solve reCAPTCHA V3 Like a Human](https://www.capsolver.com/blog/reCAPTCHA/how-to-solve-reCAPTCHA-v3)**
- **[How to Solve All Types of reCAPTCHA](https://www.capsolver.com/blog/reCAPTCHA/How-to-bypass-all-the-versions-reCAPTCHA-v2-v3)**
