

# GitHub and Posit Cloud for R

Today, we’ll set up everything so you can do all your work in a web browser from any computer. This will eliminate the need for using the HPC (High-Performance Computing) or local laptop installations, which can often be finicky.

While we can’t run all analyses via a browser in our current setup, it’s possible to run browser-based R sessions on an HPC.

---

## How to Sign Up for GitHub and Posit Cloud

This guide will walk you through the steps to create a **GitHub account** and then sign up for **Posit Cloud** (formerly RStudio Cloud).

---

### Step 1: Sign Up for a GitHub Account

1. **Go to GitHub’s Website**:
   - Open your browser and go to [https://github.com](https://github.com).

2. **Click "Sign Up"**:
   - On the top-right corner of the page, click the **Sign Up** button.

3. **Enter Your Details**:
   - Fill in the required information:
     - **Username**: Choose a unique username. *(Make this professional, as others can see it.)*
     - **Email Address**: Use your personal or school email.
     - **Password**: Create a strong password.
   - Click **Continue**.

4. **Complete the Verification**:
   - GitHub will ask you to verify your account by solving a puzzle or entering a code sent to your email.

5. **Choose Your Plan**:
   - Select the **Free Plan** (unless you need advanced features).
   - Click **Continue**.

6. **Tailor Your Experience (Optional)**:
   - Answer a few questions about your experience and interests, or skip this step.

7. **Verify Your Email**:
   - Check your email inbox for a verification email from GitHub.
   - Click the **Verify Email Address** button in the email.

8. **You’re Done!**
   - Your GitHub account is now ready to use.

---

### Step 2: Sign Up for Posit Cloud

1. **Go to Posit Cloud’s Website**:
   - Open your browser and go to [https://posit.cloud/](https://posit.cloud/).

2. **Click "Sign Up"**:
   - On the top-right corner, click the **Sign Up** button.

3. **Sign Up with GitHub**:
   - Click the **Sign Up with GitHub** button.
   - This will redirect you to GitHub to authorize Posit Cloud.

4. **Authorize Posit Cloud**:
   - Log in to your GitHub account if prompted.
   - Click **Authorize posit-cloud** to grant access.

5. **Complete Your Posit Cloud Profile**:
   - Fill in your name and create a username.
   - Agree to the terms of service and privacy policy.
   - Click **Create Account**.

6. **You’re Done!**
   - You’ll be redirected to your Posit Cloud dashboard, where you can start creating projects.

---

## Additional Setup for Posit Cloud

### Configure RStudio Settings
1. **Start a New Project**:
   - Name the new project `intro`.

2. **Adjust Global Options**:
   - Go to **Tools → Global Options**.
   - Under the **General** tab, set:
     - **Restore .RData into workspace at startup** → `Never`.
     - **Save workspace to .RData on exit** → `Never`.

---

### Uploading Data

1. **Create a Folder Structure**:
   - The default directory structure is:
     ```
     cloud/project
     ```
   - Create the following folders:
     ```
     /scripts
     /data
     /data/counts
     /results
     ```

2. **Upload Files**:
   - Upload the `.Rmd` file (e.g., `07_vargas_deseq.Rmd`) to the `/scripts` folder.
   - Upload the following files to `/data/counts`:
     - `counts_names.tsv`
     - `deseq2_input.tsv`
     - `metadata.tsv`
   - Upload `counts_archive.zip` to `/data/counts`. It will automatically unzip after uploading.

---

### Installing Packages

1. **Run the Installation Chunk**:
   - In your `.Rmd` file, run the chunk that installs the required packages:
     ```R
     required_packages <- c("BiocManager", "dplyr", "DESeq2", "ggplot2", "ggrepel")
     ```
   - This installs:
     - **BiocManager**: For installing Bioconductor packages.
     - **dplyr**: For data manipulation.
     - **DESeq2**: For differential gene expression analysis.
     - **ggplot2**: For creating visualizations.
     - **ggrepel**: For avoiding overlapping text labels in plots.

2. **Monitor Memory Usage**:
   - Note the RAM usage in the top-right corner. It may max out during installations.

---

### Loading Libraries

1. **Run the Load Libraries Chunk**:
   - After installing the packages, run the chunk that loads the libraries:
     ```R
     library(BiocManager)
     library(dplyr)
     library(DESeq2)
     library(ggplot2)
     library(ggrepel)
     ```

---

### Restarting Your Session

1. **Quit R**:
   - In the console, type `q()` to quit R.

2. **Restart Posit Cloud**:
   - Go back to the **Content** page (bookmark this page for easy access).
   - Shut the browser tab and restart your session.

3. **Reload Libraries**:
   - After restarting, reload the libraries by running the `load_libraries` chunk again.

---

### Troubleshooting Memory Issues

1. **Check Memory Usage**:
   - Use the following command to see which objects are taking up the most memory:
     ```R
     sapply(ls(), function(x) object_size(get(x)))
     ```

2. **Copy the Project**:
   - If your project is lagging or crashing, copy it and start fresh with the copied version. Give it a new name.

---

### Knitting to HTML

1. **Avoid the Knit Button**:
   - The **Knit to HTML** button in Posit Cloud can be problematic. Instead, use this command:
     ```R
     rmarkdown::render("/cloud/project/scripts/07_vargas_deseq.Rmd", output_dir = "/cloud/project/results")
     ```

---

### Sharing Your Project

1. **Make Your Project Public**:
   - Go to your Posit Cloud dashboard.
   - Click the **gear icon** next to your project.
   - Select **Make Public**.

2. **Share the Link**:
   - Share the project link (e.g., `https://posit.cloud/content/9871403`) with others.

---

## Summary

- **GitHub and Posit Cloud** allow you to work in a browser from any computer.
- **Install and load packages** as needed.
- **Monitor memory usage** to avoid crashes.
- **Knit to HTML** using the `rmarkdown::render()` command.
- **Share your project** by making it public and sharing the link.
