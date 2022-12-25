---
title: Setup Custom Domain for S3 Wasabi
date: 2022/12/23
tags: [cdn, wasabi, s3, cloudflare]
categories: [S3, Wasabi]
---
This is Wasabi and Cloudflare integration guide

<!-- more -->
# Note:

The information in red is important information, so save it to avoid loss.

(**Bucket Name, Endpoint , Access Key and Secret Key**)


![wasabi-cf](https://cdn.discordapp.com/attachments/786432484144840746/1055754811565416538/wsbcf.jpg)


# Setup Bucket S3 Wasabi



Click on **Create Bucket**

**Bucket Name**: to sub domain of main domain

**Select Region:** Select Region as close to server as possible, then copy and save url region, that is Endpoint

Click **Next** repeatedly, go to **Step 3** ![enter image description here](https://lh5.googleusercontent.com/dQIcneZhfKp_rZCO_ao-X3Lt4_wRXPXc6qwFZtX-G6z0Y0lcAGhO6H05cNVoWdyG1VsEiEA2bd22YJr-Tt-5g6aaJy8FoaQGYc-jmoyAGrBVPWfPTwVutcjZlJFFMGS7-iZn-BDpRVs3buKcbUn4MMtVK5iBk3TGG4mJl1PmrLLDztjo4IL18dUJBuIPQw)And click **Create Bucket** to finish.

# Create a folder containing images

Click to create a folder, name it images as shown.

![](https://lh6.googleusercontent.com/RKJZsOcPNswifpkiGBBm2y1RqvjCHfuruEN-2nvVfogV5GlpFZpkIYT0R6OCAhkK7OQD8NkEQ3DPceFufXkxkY9gdLVBwDYFHX-MaL5I5l2G6_QvnS5rhjawGS-Z0fF7CC6Cy5GpJ5TxaxpS53w__HD9RmyQolacyYleTl0OCGpcUpmUjWLkPg84hI6R_g)

![](https://lh4.googleusercontent.com/kmcaETQVKufI1EcQHPSL_JSASAtywWKj05tzYUXq05HonV0M8CJTjVZpSML_dmywVgYfLeV3nPmY3AUAHsLbEn6Y3tL1mwmCEgPQbcBPSmZ7gIv2sAw0IQn0CwPpVmUg5daqa5zy2Edt3C4INP8UBJec2MG1eQjTeOrojcncwx5-1wzU-Bq1SsHBufMsqQ)

# Configure Bucket S3 Wasabi![enter image description here](https://lh6.googleusercontent.com/-n5eKh011rVzDDCHLSIRYMQt1DbPBvOAEc2zbdxk4jaG8lmiOvaDtjI3J5ecGxxF6AuaZD0eFJFogQnoypPAWhd-KR8_pwbGCQLq1reEfQFekdIEikSNxm4ceNWa_D7anS1xJK6Q4M-JoqGYe6-mUkEu5YyqfD2g2xjCTtGL-lzXOxE7Z2rRypgcGpT1SQ)

Click on the Bucket newly created

![enter image description here](https://lh4.googleusercontent.com/mskWDyv19CG3QnbbctpMqT7P-OsIMi9QRu_kr4PD2H5Zr0XexSrXlSMaMBNOqWe5-DJ7kK7u4x5X1tuKqgSQV6Bx0F78XOKtIu0ie_OiGYyP_VbkbiiMNy4H918KrOuPK0152TqLxHEPMe0PoLZJCcN84-PwsWglFGDZfOFNHwaAu97VDl1o_lye_qO6iQ)

Click on **settings** (gear image).

![enter image description here](https://lh4.googleusercontent.com/dB7AhgfUMH5Xoq32PZbN0198Ka2KbUxgi1gtGuezmsbdCaw7qJFEiYW_cPE_3t2mVCVbzg3oNlTwoiz5i2zZzohocO47e6Auo9Jucf0I9PHig1fbBZCkbuMBzIgmF1YnukHdDRcu8iS-oYZtTtdbGXJam7vASxWaNe0u4imKCwc_nPACx-Ra3gdJGUaSyg)

Copy the code below
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": [
        "s3:GetObject",
        "s3:GetObjectVersion"
      ],
      "Resource": "arn:aws:s3:::my.mydomain.com/*"
    }
  ]
}
```

Then go to the **POLICIES**

Paste the **Policies** , remember to replace *my.mydomain.com* with your sub domain, then **Save** again

![enter image description here](https://lh5.googleusercontent.com/6v0DVpijZqbWv9cuOKQ72mOnF9XYeAT5dp7gHDCAf607NY3vLDLxIm5oJNyhazogtYDWHqY9o-mEdyO2GMvrnB9zevBLFV1m3FipAP9_XNynfxa9yZQBABUlngDwU2AjjjQAHC-PAPrTJ9AGOwKph4k4jdt6wBdycyRvPJUZqny4JgOaWowQxEKuHNCx_Q)

# Get Access Key

Into **Access Keys**  ->  **Create New Access Key** ![enter image description here](https://lh5.googleusercontent.com/BDNSo4ZvIf39obz7DB2jWdy2m-K37hcJBbCVtSeGKBmRAgod2icxkcUvHCNrGQxHZVJhLrePwXan1laUzIz8JFJcl2Nw2jJKtFRaGRw3loLTz7Ue6mdqSLBupNZOev6NgVy-p04_D5244XPolK9JNviB5EZecyP85VTd5Qk3wQb9TOsp3pLOetwMh0LmnQ)

![](https://lh4.googleusercontent.com/fyTEPU7lDBE2hOxMDVrKgkkoA-9EIuXlVfbwC6IKYknlN5hLWTyZHD1mYFJkJ3QvSBGVSjqJnh8CQAMNOFOP9qzNCC9HrWfuWpDbdQcPvetMNtqGNTV_7lq5wwqKJ3JvpXaSXXw3gzwsTENlSxnGelBSPj9fT6aaEcTb8cV0syQUQJYIs3LGDfjaldS1Hw)

![enter image description here](https://lh3.googleusercontent.com/_uy5dHBEZVH2S6NBCCS3MU0oH6-dHuQY8FirsQhhyZQ2pkiWEoh3yiEM651X6rbuSEi8o4bz2ANEV5rsIgiDCfIHAWev2XdAM7l_hvJ29WjSHoTRV91BrKI0FSAMxGoKjl7XIiGpZsIS1EsXFMWdVtXJ6yFE7TMsgAZKjFaN4Co1qTVf6InXnJ9c3iJJ0A)

Click Show in **Secret Key** to display Key Save 2 important information **Access Key** and **Secret Key** to **S3 Wasabi**

Add 1 **CNAME** as follows:

Name: enter subdomain (eg: want subdomain to be cdn. mydomain.com, just enter cdn) Target: enter the url endpoint when creating the bucket

Then click **Save**.

![enter image description here](https://lh5.googleusercontent.com/yRFb-rw7L59-tXxhZS74kMLeLs-a1i91JaVPiv8ZkYrlck8KB2bbvU0WY8YSOYMiOp3wG1pQpuprctbn1sEZg9KCQABEbXyXOqXEPF_HJFIYplvRBEthREHgVCqK_XV3HRAF5FndzGF-kiaUtfxGguUlKni-WoJIc3agNCv0lSBWpG9PZku3Pqx5om4mtQ)

# Required Information

To connect to **S3 Wasabi**, you need the following

**Bucket Name**: cdn.mydomain.com (bucket Name is also sub domain)

**Endpoint**: [https://ap-southeast-1.wasabisys.com](https://ap-southeast-1.wasabisys.com/) ( Endpoint taken from url region in step 1)

**Access** **Key**: `PSENEVL40B513GQRAUXA`

**Secret Key**: `aSvu9YjHbMjsBytyaJ1KtvO4LyCCcq1G48Oz0bXu`

  
 

