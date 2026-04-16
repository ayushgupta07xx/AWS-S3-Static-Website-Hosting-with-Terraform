# AWS S3 Static Website Hosting with Terraform

This Terraform project automates the deployment of a static website on Amazon S3 with public access and static website hosting configuration.

## 📋 Project Description

This infrastructure-as-code solution creates a fully functional static website hosted on AWS S3. It handles bucket creation with unique naming, public access configuration, website hosting setup, and automatic file uploads.

## 🏗️ Architecture Overview

### AWS Resources Created
- **S3 Bucket**: Dynamically named bucket using random ID generation (`mywebapp-bucket-{random_hex}`)
- **Bucket Policy**: Public read access policy for website content
- **Public Access Block**: Configured to allow public access
- **Website Configuration**: Enabled with `index.html` as the default document
- **S3 Objects**: Automated upload of `index.html` and `styles.css` files

### Deployment Region
- **Region**: Tokyo (`ap-northeast-1`)

## ✨ Features

- ✅ Automatic bucket naming with random ID to ensure uniqueness
- ✅ Public access configuration for website hosting
- ✅ Static website hosting enabled with proper index document
- ✅ Automated file uploads with correct content types
- ✅ Public read policy for anonymous website access
- ✅ Output provides direct website endpoint URL

## 📁 Project Structure

```text
proj-static-website/
├── main.tf        # Main Terraform configuration (Provider, S3, Policies)
├── index.html     # Website homepage
├── styles.css     # Website styles
└── README.md      # Project documentation
```

## 🚀 Usage

### Prerequisites
- Terraform installed (v1.0+)
- AWS CLI configured with valid credentials
- Appropriate AWS IAM permissions for S3

### Deployment Steps

```bash
# Initialize Terraform
terraform init

# Preview the infrastructure changes
terraform plan

# Deploy the infrastructure
terraform apply
```
Visit this URL in your browser to view your static website.

## 📤 Outputs

- `name`: The S3 website endpoint URL for accessing the deployed static website

## 🎨 Customization

### Modify Website Content

1. Edit `index.html` for content changes
2. Edit `styles.css` for styling updates
3. Run `terraform apply` to upload changes

### Add More Files

Add additional S3 object resources in `main.tf`:

```hcl
resource "aws_s3_object" "your_file" {
  bucket       = aws_s3_bucket.mywebapp-bucket.bucket
  source       = "./your-file.js"
  key          = "your-file.js"
  content_type = "application/javascript"
}
```

### Change Region

Modify the provider region in `main.tf`:

```hcl
provider "aws" {
  region = "us-east-1"  # Change to your preferred region
}
```

## 🧹 Clean Up

To destroy all resources and avoid AWS charges:

```bash
terraform destroy
```

## 📝 Notes

- The S3 bucket is configured for public access - ensure no sensitive data is uploaded
- Bucket names are globally unique across AWS
- Static website hosting only supports HTTP (not HTTPS by default)
- For HTTPS, consider adding CloudFront distribution

## 🔒 Security Considerations

- Public read access is enabled - only host public content
- Consider enabling versioning for content management
- Review bucket policies before production deployment
- Implement CloudFront with ACM certificate for HTTPS

## 📚 Additional Resources

- [AWS S3 Static Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
- [Terraform AWS Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [S3 Bucket Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-bucket-policies.html)

## 👤 Author

**Ayush Gupta** - VIT-Vellore

## 📄 License

This project is open source and available for educational purposes.





