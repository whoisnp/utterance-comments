# Blog Commenting with Utterances

This Project is a POC which explains how I integrated the [Utterances](https://utteranc.es/) commenting system into my Next.js project.

## Overview

Utterances is a lightweight commenting system that uses GitHub issues to store comments. It is easy to set up and integrates seamlessly with static sites.

## Steps to Integrate Utterances

### 1. Create a GitHub Repository
- Create a new GitHub repository (or use an existing one) to store the comments.
- Ensure the repository is public, as Utterances requires public repositories to function.

### 2. Install Utterances
- Visit the [Utterances website](https://utteranc.es/).
- Configure the settings:
    - Select your GitHub repository.
    - Choose a mapping option (e.g., `pathname`, `url`, or `title`).
    - Copy the generated `<script>` tag.

### 3. Add Utterances to Your Next.js Project
- Open the Next.js project and navigate to the blog post page component (e.g., `pages/blog/[slug].js`).
- Add the Utterances `<script>` tag to the component. Example:

```jsx
import { useEffect } from 'react';

const BlogPost = ({ post }) => {
    useEffect(() => {
        const script = document.createElement('script');
        script.src = 'https://utteranc.es/client.js';
        script.async = true;
        script.setAttribute('repo', 'your-username/your-repo');
        script.setAttribute('issue-term', 'pathname'); // Adjust based on your mapping
        script.setAttribute('theme', 'github-light'); // Choose a theme
        script.crossOrigin = 'anonymous';
        document.getElementById('comments').appendChild(script);
    }, []);

    return (
        <div>
            <h1>{post.title}</h1>
            <p>{post.content}</p>
            <div id="comments"></div>
        </div>
    );
};

export default BlogPost;
```

### 4. Test the Integration
- Run your Next.js project locally (`npm run dev`).
- Navigate to a blog post and verify that the Utterances comment box appears.
- Ensure comments are being stored as issues in your GitHub repository.

### 5. Deploy the Project
- Deploy your Next.js project to your hosting platform (e.g., Vercel).
- Verify that the commenting system works on the live site.

## Customization
- You can customize the theme of the comment box by changing the `theme` attribute in the script tag.
- Supported themes include `github-light`, `github-dark`, `preferred-color-scheme`, etc.

## Troubleshooting
- Ensure the GitHub repository is public.
- Verify that the `repo` and `issue-term` attributes in the script tag are correctly configured.
- Check the browser console for errors if the comment box does not load.

## Conclusion
Integrating Utterances into a Next.js project is straightforward and provides a GitHub-powered commenting solution for your blog.
