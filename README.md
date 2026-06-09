# Samizdat-Plugin-Nets

Nets (Nexi) card payments — an **operator** payment module for [Samizdat](https://fakenews.com).
Used by Samizdat-Plugin-Invoice (helper-guarded) to take payment on invoices.
Extracted from the monorepo with history.

## Layout

    lib/Samizdat/Plugin/Nets.pm        routes + the `nets` helper
    lib/Samizdat/Controller/Nets.pm    request handlers (incl. webhook/callback)
    lib/Samizdat/Model/Nets.pm         payment API client
    lib/Samizdat/resources/templates/nets/    views
    lib/Samizdat/resources/settings/nets/     JSON-Schema config (operator; writeOnly secrets)
    lib/Samizdat/resources/locale/nets/       translations
    lib/Samizdat/resources/migrations/pg/   the `nets` schema (fresh-snapshot migration)

## Dependencies

- **Samizdat** (core) — Cache, settings resolver, the migration loader. Not on CPAN; PERL5LIB or install.
- Mojolicious, Hash::Merge.

## Install

    perl Makefile.PL && make && make test    # core on PERL5LIB
    make install

Enable via `extraplugins: [Nets]` and configure `manager.nets` (API keys/secrets;
certs are deployment secrets, never shipped here).
