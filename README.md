# How to Host a Static Website Using S3

## ❓ Challenge :
Hosting a static website requires a reliable, scalable, and cost-effective solution. AWS S3 provides a simple way to host static websites without the need for server management, making it an ideal choice for developers. Let's explore how to achieve this!

## 💡 Approach :
We will use an AWS S3 bucket to store and serve static files (HTML, CSS, JavaScript). By enabling S3's static website hosting feature and configuring necessary permissions, we can make the website publicly accessible.

## 👁 Observation :
While S3 is a great hosting solution for static websites, we also need to consider security, performance optimization, and cost management. Additional services like 
- <b>CloudFront</b> (for CDN), <br>
- <b>Route 53</b> (for custom domains), and <br>
- <b>IAM</b> (for access control) can enhance our setup.

## 🪜 Steps :

### Step 1: Create an S3 Bucket
- Go to the AWS Management Console.
- Navigate to S3 and click "Create bucket."
- Provide a <b>unique bucket</b> name.<br>
  ![image](https://github.com/user-attachments/assets/18133cee-36d3-4a69-8a28-766c1d48cb69)<br><br>

- Disable "Block all public access" to allow public access to website files.
- Click "Create bucket".<br>
 ![image](https://github.com/user-attachments/assets/c2cce12d-1f4f-4519-8eee-0e05b8c7e2fb)<br><br>

### Step 2: Upload Website Files
- Upload your `index.html`, `styles.css`, and other necessary files to the bucket.
- Set appropriate permissions for these files to be publicly readable.<br>
  ![image](https://github.com/user-attachments/assets/2cebaf0e-f577-4eb7-86fe-3df99a578c9e)<br><br>


### Step 3: Enable Static Website Hosting
- In the S3 bucket settings, go to the "Properties" tab.
- Scroll down to "Static website hosting" and enable it.
- Set the index document (e.g., `index.html`).
- Click "Save Changes".<br>
![image](https://github.com/user-attachments/assets/21e42c90-744f-4361-a4c1-55fe3e776e99)<br><br>
- Note the Endpoint URL provided by AWS.<br>
![image](https://github.com/user-attachments/assets/d95124a4-009d-4460-b245-d4a719cd1824)<br><br>


### Step 4: Update Bucket Permissions for Public Access
- Go to the "Permissions" tab of your S3 bucket.
- Click on "Bucket Policy" and add the following policy:
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Principal": "*",
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::your-bucket-name/*"
      }
    ]
  }
  ```
- Replace `your-bucket-name` with your actual bucket name. (in my case, it is "mystaticwebsite-demogit")<br>

![image](https://github.com/user-attachments/assets/fe845e4b-5e38-40b0-bbe9-95b8efcfebb9)<br><br>

- Click "Save changes".
  
### Step 5: Access Your Website
- Use the endpoint URL provided in Step 3 to access your static website.
- If you forgot to note down, Go to "Properties" and look under "Static website hosting", you'll find the link.  VOILA! 🎉<br>
  ![image](https://github.com/user-attachments/assets/ba3acc2f-51b4-40d2-8dba-c40cacd7dde4)<br><br>


### Step 6: (Optional) Use a Custom Domain with Route 53
- Register a domain via Route 53 or use an existing domain.
- Create an alias record in Route 53 pointing to your S3 bucket.


## 🔍 Architectural Insights:
Additionally, we can use 'Amazon CloudFront' as a Content Delivery Network (CDN) to distribute content with lower latency. This helps in reducing the load on the S3 bucket and provides better performance for users across different regions. However, enabling CloudFront introduces <b>additional costs</b>, so it's important to analyze the cost-benefit trade-off. 

<b>NOTE:</b> Using S3 alone may be a **better choice** for small-scale projects where global distribution is not a priority.


## ✅ Conclusion :
By following these steps, we successfully hosted a static website using AWS S3. With additional configurations like Route 53 for custom domains and CloudFront for CDN, we can further optimize the website for better performance and security!

<h3> 🟢Happy Learning ! 🥁🙌🫶 </h3>


