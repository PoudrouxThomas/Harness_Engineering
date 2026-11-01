# Node 24, .NET 10 and Postgres 16 are pinned identically everywhere

Cloud sessions preinstall Node 20 to 22 and no .NET, and ship Postgres 16. To keep local, CI and cloud runs identical, versions are pinned (`.nvmrc`, `engines`, `global.json`, committed lockfiles), the cloud setup script installs Node 24 and .NET 10, and Postgres is fixed at 16 to match the cloud's preinstalled one.
