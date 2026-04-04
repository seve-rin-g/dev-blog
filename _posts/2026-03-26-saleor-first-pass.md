---
title: Using Saleor for Open-Source e-commerce site
tags: [Software Development, e-Commerce, Saleor, GraphQL, Next.js]
style: fill
color: info
description: goal is to make a site for a's leatherworking with pricing and cart integration

---

# First project with Saleor

My goal is to make a site for A’s leatherworking that can function like both a portfolio and an avenue for purchases (with pricing and cart integration). This is my first e-commerce site outside of using a platform like BigCartel for other merch vendors.

(Saleor is a GraphQL native, API-only platform for scalable composable commerce.)

I ultimately want to host on AWS, but doing this locally for now. 

## Result

![result]({{"/assets/images/saleor-local-frontend.jpg" | absolute_url}})

This worked well and the Docker container runs locally. 

Next steps: 
1. Deploy to AWS
2. Set up Payment integration with Stripe or Paypal

## Backend setup

I followed the walkthrough from https://docs.saleor.io/quickstart/running-locally

> Add the cloned saleor-platform directory to the list of shared directories in Docker (Settings -> Shared Drives or Preferences -> Resources -> File sharing).

(This step failed without a pro account, but I was able to proceed to the end.)

```
git clone https://github.com/saleor/saleor-platform.git
cd saleor-platform
docker compose pull
```

Apply database migrations:
```
docker compose run --rm api python3 manage.py migrate
```

Optionally, populate the database with sample data:
```
docker compose run --rm api python3 manage.py populatedb
```

Finally, create an admin account:
```
docker compose run --rm api python3 manage.py createsuperuser
```

(Note: in the docs, the createsuperuser step above is supposed to set admin@example.com and admin automatically, but for me it prompted in terminal to enter an email and password.
)

Run app via `docker compose up`

Now the backend is running (default http://localhost:9000), which includes a dashboard that the vendor would use to track purchases, shipping status, and update items in the DB. 

## How to Setup Frontend 

Saleor also has a feature called [storefront](https://github.com/saleor/storefront?tab=readme-ov-file) which you can use as the shop frontend (or you could use a different frontend as long as you connect to the Saleor GraphQL API). 

### Modified `.env` 

I edited the frontend `.env` file to refer to my local graphql deployment.

### Installed Next.js
```
corepack enable pnpm
pnpm install
```
### Run frontend in dev mode
```
pnpm dev
```

When adding a new product to the backend, it won't show up in the frontend until it's enabled as "viewable". 

Error with to fix “⨯ upstream image http://localhost:1337/uploads/image.png resolved to private ip ["::1","127.0.0.1”]” -- this wouldn't be an issue when deployed. 

CORS workaround I used for development:

```
images: {
    dangerouslyAllowLocalIP: true,
}
```

Now I have local frontend and backend integration.