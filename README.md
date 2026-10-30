# AEGIS AI --- Mobile Cyber Defense Companion

> **Don't just detect the threat. Investigate the evidence.**

AEGIS AI is a mobile-first cybersecurity companion designed to help
users recognize suspicious links and understand the risks behind them.
It combines immediate, on-device/mobile protection workflows with a
deeper web-investigation layer powered by **TinyFish**.

The project was presented by **Team Fs0ci3ty** at the TinyFish
Hackathon, organized by **Igniteroom** at **Presidency University,
Bangalore**.

## Table of Contents

-   [The Problem](#the-problem)
-   [Our Approach](#our-approach)
-   [Key Features](#key-features)
-   [How It Works](#how-it-works)
-   [TinyFish Integration](#tinyfish-integration)
-   [Architecture](#architecture)
-   [Safety and Privacy](#safety-and-privacy)
-   [Project Status](#project-status)
-   [Team](#team)

## The Problem

A suspicious message may contain a URL, but the URL alone rarely
explains what happens after a user opens it. Fraudulent websites can use
redirects, imitate trusted brands, and display fake login or payment
prompts.

A risk score or warning is useful, but users also need understandable
evidence explaining **why** a destination may be unsafe.

## Our Approach

AEGIS AI uses two complementary layers:

1.  **Local protection:** monitors supported notification events,
    extracts candidate URLs, runs the app's existing local detection
    workflow, and presents a warning with a risk score.
2.  **Web investigation:** uses TinyFish-powered browser intelligence to
    inspect a validated public URL, observe redirects and visible page
    content, and produce evidence that can support a clearer risk
    assessment.

The local warning is intended to appear immediately. The web
investigation adds context and does not replace local protection.

## Key Features

-   **Phishing URL detection** --- identifies suspicious links and
    presents security warnings.
-   **Notification monitoring** --- monitors supported notification
    events and surfaces candidate URLs.
-   **TinyFish-powered website investigation** --- investigates public
    web destinations, redirects, and visible page content.
-   **APK and application risk analysis** --- presents application
    permission-risk information; the demonstration also showed a
    VirusTotal result.
-   **Security event dashboard** --- displays live security events and
    local scan outcomes.
-   **Evidence-oriented reports** --- organizes observations such as
    destination changes, page content, and risk indicators to help users
    understand a warning.

> Feature availability can depend on the current build and configured
> services. Do not assume every planned capability is enabled in every
> deployment.

## How It Works

A typical investigation flow is:

1.  A suspicious link arrives in a supported notification.
2.  The local detection workflow evaluates the candidate URL.
3.  The user starts a deeper investigation when needed.
4.  The TinyFish browser agent visits the validated public destination.
5.  The investigation gathers available observations, such as redirects
    and visible page content.
6.  Findings and limitations are presented so the user can make a safer
    decision.

An investigation report may include:

-   The observed destination URL
-   Redirect or navigation observations
-   Relevant visible page content
-   Suspicious prompts or impersonation indicators
-   Evidence limitations and recommended next steps

## TinyFish Integration

TinyFish provides the web-intelligence layer for deeper investigation.
The presentation describes the use of:

-   **Browser Agent** to navigate and inspect public pages.
-   **Search** to discover relevant public sources.
-   **Fetch** to retrieve content from known pages.
-   **Research** to synthesize information across sources.

The intended outcome is to move beyond a simple "suspicious" label and
provide observations that explain what the destination showed.

**Implementation note:** The project presentation distinguishes the
demonstrated local-protection foundation from the TinyFish investigation
integration/roadmap. Verify the current source code and live deployment
before describing the TinyFish workflow as fully operational.

## Architecture

The proposed architecture separates the mobile client, secure backend,
TinyFish services, and evidence storage.

  -----------------------------------------------------------------------
  Component                           Responsibility
  ----------------------------------- -----------------------------------
  Android client                      Notification listener, local
                                      detection, warning and
                                      investigation interface

  Secure backend                      URL validation, investigation job
                                      handling, persistence, rate
                                      limiting, and report API

  TinyFish services                   Browser-based investigation and
                                      supporting search, fetch, and
                                      research capabilities

  Evidence store                      Investigation status, observed
                                      evidence, and sanitized reports
  -----------------------------------------------------------------------

The backend is designed to keep the TinyFish API key server-side,
validate investigation targets, and return sanitized findings to the
application.

## Safety and Privacy

AEGIS AI is designed around the following investigation safeguards:

-   Investigate public HTTP/HTTPS destinations only.
-   Block private and internal network destinations.
-   Revalidate redirect destinations.
-   Never enter passwords, OTPs, payment details, or submit forms.
-   Treat website content as untrusted data, not as instructions to the
    agent.
-   Keep service API keys on the backend.
-   Minimize notification data and sanitize investigation reports.
-   Treat blocked pages, CAPTCHAs, timeouts, and incomplete observations
    as inconclusive rather than proof of safety or maliciousness.
-   Preserve local detection as a fallback when the network or
    investigation service is unavailable.

## Project Status

AEGIS AI was presented as a working foundation with a roadmap for
expanding web intelligence. The presentation identifies the following
future directions:

-   Scam campaign research
-   Shopping-scam and fake-support checks
-   Website change monitoring
-   Evidence-backed relationships between suspicious sites
-   A plain-language AI investigation assistant

These are proposed extensions and should not be represented as completed
features unless verified in the current build.

## Team

**Team Fs0ci3ty**

-   Pratham
-   Yashin
-   Yousuf

## Acknowledgements

Thanks to **Igniteroom**, **TinyFish**, and **Presidency University**
for the opportunity to participate in the TinyFish Hackathon and present
AEGIS AI.

------------------------------------------------------------------------

*AEGIS AI --- Turning suspicious links into evidence-led
investigations.*
