# SEMO
SEMO website is a social media website that will help people to chat and post media like photos and videos
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SEMO</title>
    <style>
        /* Inline CSS */
        body {
            font-family: Arial, sans-serif;
        }
        .post {
            border: 1px solid #ccc;
            padding: 10px;
            margin: 10px;
        }
    </style>
</head>
<body>
    <h1>WELCOME TO SEMO</h1>

    <!-- Post Form -->
    <form id="postForm">
        <label for="postText">Create a new post:</label>
        <textarea id="postText" rows="4" cols="50"></textarea><br>
        <button type="button" onclick="createPost()">Post</button>
    </form>

    <!-- Posts Container -->
    <div id="postsContainer"></div>

    <script>
        // Sample data for posts (you'd replace this with data from a server in a real app)
        const samplePosts = [
            { username: "User1", text: "This is post 1" },
            { username: "User2", text: "This is post 2" },
        ];

        // Function to create a new post
        function createPost() {
            const postText = document.getElementById("postText").value;
            if (postText.trim() === "") {
                alert("Please enter some text for your post.");
                return;
            }

            const post = {
                username: "User1", // You can replace this with the logged-in user's username
                text: postText,
            };

            // Add the new post to the samplePosts array (in a real app, you'd send it to the server)
            samplePosts.push(post);

            // Clear the textarea
            document.getElementById("postText").value = "";

            // Update the posts on the page
            displayPosts();
        }

        // Function to display posts
        function displayPosts() {
            const postsContainer = document.getElementById("postsContainer");
            postsContainer.innerHTML = "";

            samplePosts.forEach((post, index) => {
                const postElement = document.createElement("div");
                postElement.className = "post";
                postElement.innerHTML = `
                    <p><strong>${post.username}</strong></p>
                    <p>${post.text}</p>
                `;
                postsContainer.appendChild(postElement);
            });
        }

        // Initial display of posts
        displayPosts();
    </script>
</body>
</html>
