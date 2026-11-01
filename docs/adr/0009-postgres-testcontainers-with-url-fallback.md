# Tests use Postgres via Testcontainers, with a `TEST_DB_URL` override

Tests run against a real, throwaway Postgres rather than SQLite, so behaviour matches production and parallel worktrees never share state. Docker exists in cloud sessions but Testcontainers there is unverified, so the test fixture uses an externally provided database when `TEST_DB_URL` is set (for example the cloud's preinstalled Postgres).
