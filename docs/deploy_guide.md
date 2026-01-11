# Deploying Thunderdome to Render

This guide explains how to deploy your Thunderdome Planning Poker instance to [Render.com](https://render.com) using the included `render.yaml` Blueprint.

## Prerequisites

1.  **Render Account**: Create a free account at [https://render.com](https://render.com).
2.  **GitHub Repository**: Ensure this code is pushed to a GitHub repository that you have access to.

## Deployment Steps

1.  **Commit & Push**: Ensure your latest changes (including `render.yaml`) are committed and pushed to your GitHub repository.
2.  **Dashboard**: Log in to the Render Dashboard.
3.  **New Blueprint**: Click the **New +** button and select **Blueprint**.
4.  **Connect Repo**: Connect your GitHub account and select your Thunderdome repository.
5.  **Service Name**: Give your blueprint service a name (e.g., `my-planning-poker`).
6.  **Apply**: Click **Apply**. Render will automatically:
    *   Create a PostgreSQL database (Free Tier).
    *   Create a Docker Web Service (Free Tier).
    *   Link them together securely.

## Environment Variables

The `render.yaml` sets up the essential variables. You can configure additional ones in the Render Dashboard under **Environment**:

*   **ADMIN_EMAIL**: Set this to your email to become the initial Super Admin.
*   **SMTP_***: Configure these if you want to enable email notifications (requires an external SMTP provider like Mailgun, SendGrid, or AWS SES).

## Troubleshooting

*   **Build Failures**: Check the logs in the Render dashboard. Ensure the Docker build is working locally.
*   **Database Connection**: Ensure `DB_SSLMODE` is set to `require` (default in our `render.yaml`) as Render Postgres requires SSL.
