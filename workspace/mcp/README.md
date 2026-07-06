# MCP (Model Context Protocol) সেটআপ গাইড

এই ডিরেক্টরি এবং ডকুমেন্টেশনটি ফিউচার MCP ইন্টিগ্রেশনের প্রস্তুতি হিসেবে তৈরি করা হয়েছে। Hermes-এর সাথে বিভিন্ন অফিসিয়াল MCP সার্ভার কিভাবে সংযুক্ত করতে হবে তা নিচে বর্ণনা করা হলো।

ক্রেডেনশিয়াল এবং সংবেদনশীল তথ্যসমূহ প্রজেক্টের রুট ডিরেক্টরিতে থাকা `.env` ফাইলে কনফিগার করতে হবে।

---

## ১. Filesystem MCP
লোকাল ফাইল সিস্টেমে প্রবেশের অনুমতি প্রদানের জন্য এই সার্ভারটি ব্যবহৃত হয়।

- **উদ্দেশ্য:** প্রজেক্টের ডেটা বা রিপোর্ট ফোল্ডারে ফাইল রিড/রাইট করা।
- **কনফিগারেশন:** `.env` ফাইলে `MCP_FILESYSTEM_ALLOWED_PATHS` ভ্যারিয়েবলে অনুমোদিত ফোল্ডারের অ্যাবসোলিউট পাথ উল্লেখ করুন।
- **কানেকশন কমান্ড:**
  ```json
  {
    "mcpServers": {
      "filesystem": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-filesystem", "E:/xampp/htdocs/Projects/Hermes/data"]
      }
    }
  }
  ```

---

## ২. GitHub MCP
গিটহাব রিপোজিটরি অটোমেশন, ইস্যু তৈরি, পিআর (Pull Request) ম্যানেজমেন্ট এবং কোড সার্চ করার জন্য এটি ব্যবহৃত হয়।

- **উদ্দেশ্য:** রিপোজিটরি অটোমেশন।
- **ক্রেডেনশিয়াল:** গিটহাব অ্যাকাউন্ট থেকে একটি **Personal Access Token (PAT)** জেনারেট করে `.env` ফাইলে `MCP_GITHUB_PERSONAL_ACCESS_TOKEN` হিসেবে যুক্ত করুন।
- **কানেকশন কমান্ড:**
  ```json
  {
    "mcpServers": {
      "github": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-github"],
        "env": {
          "GITHUB_PERSONAL_ACCESS_TOKEN": "your_token_here"
        }
      }
    }
  }
  ```

---

## ৩. Browser Automation MCP (Playwright)
ব্রাউজার অটোমেশনের মাধ্যমে ওয়েব পেজ স্ক্র্যাপিং, স্ক্রিনশট নেওয়া এবং ডাইনামিক ওয়েব ইন্টারঅ্যাকশন করতে এটি ব্যবহৃত হয়।

- **উদ্দেশ্য:** ওয়েব রিসার্চ এবং ব্রাউজার টেস্ট।
- **ক্রেডেনশিয়াল ও ডিপেন্ডেন্সি:** উইন্ডোজ বা লিনাক্সে Playwright এবং Chromium ব্রাউজার ইনস্টল থাকতে হবে।
- **কানেকশন কমান্ড:**
  ```json
  {
    "mcpServers": {
      "playwright": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-postgres"] 
        // নোট: ব্রাউজার অটোমেশনের জন্য প্লেরাইট স্ক্রিপ্ট রান করানো হয়
      }
    }
  }
  ```

---

## ৪. PostgreSQL MCP
পোস্টগ্রেস ডেটাবেজে কোয়েরি চালানো, টেবিল স্ট্রাকচার এবং ডেটা রিড/রাইট করার জন্য ব্যবহৃত হয়।

- **উদ্দেশ্য:** নলেজ বেস এবং কাস্টমার ডেটা স্টোর করা।
- **ক্রেডেনশিয়াল:** ডেটাবেজের হোস্ট, পোর্ট, নাম, ইউজার এবং পাসওয়ার্ড `.env` ফাইলে কনফিগার করুন।
- **কানেকশন কমান্ড:**
  ```json
  {
    "mcpServers": {
      "postgres": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://username:password@localhost:5432/database_name"]
      }
    }
  }
  ```

---

## ৫. Google Drive MCP
গুগল ড্রাইভ ফাইল অ্যাক্সেস, ডকুমেন্ট তৈরি এবং ড্রাইভ সার্চ করার জন্য ব্যবহৃত হয়।

- **উদ্দেশ্য:** গুগল ডক্স এবং ড্রাইভের সাথে ইন্টিগ্রেশন।
- **ক্রেডেনশিয়াল:** Google Cloud Console থেকে API সক্রিয় করে Client ID, Client Secret এবং Refresh Token নিয়ে `.env` ফাইলে বসান।
- **কানেকশন কমান্ড:**
  ```json
  {
    "mcpServers": {
      "google-drive": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-google-drive"],
        "env": {
          "GOOGLE_CLIENT_ID": "your_client_id",
          "GOOGLE_CLIENT_SECRET": "your_client_secret",
          "GOOGLE_REFRESH_TOKEN": "your_refresh_token"
        }
      }
    }
  }
  ```

---

## ৬. Web Search MCP
সার্চ ইঞ্জিন থেকে লাইভ সার্চ রেজাল্ট এবং ডেটা রিট্রিভ করার জন্য এটি ব্যবহৃত হয়।

- **উদ্দেশ্য:** গুগল সার্চ এবং লাইভ রিসার্চ।
- **ক্রেডেনশিয়াল:** Tavily API Key বা Google Custom Search Engine (CSE) ক্রেডেনশিয়াল `.env` ফাইলে বসান।
- **কানেকশন কমান্ড (Tavily):**
  ```json
  {
    "mcpServers": {
      "tavily-search": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-tavily-search"],
        "env": {
          "TAVILY_API_KEY": "your_tavily_key"
        }
      }
    }
  }
  ```
