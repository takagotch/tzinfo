### tzifno
---
https://github.com/tzinfo/tzinfo

```ruby
gem 'tzinfo-data'
gem 'tzinfo-data', platforms: [:mingw, :mswin]
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
gem 'tzinfo-data', platforms: [:mingw, :mswin, :jruby]
gem install tzinfo-data

TZInfo::DataSource.set(:zoneinfo, zoneinfo_path)

```

```ruby
require 'tzinfo'
identifiers = TZInfo::Timezone.all_identifiers

tz = TZInfo::Timezone.get('America/New_York')

tz.to_local(Time.utc(2018, 2, 1, 12, 30, 0))
tz.to_local(Time.utc(2018, 7, 1, 12, 30, 0))
tz.to_local(Time.new(2018, 7, 1, 13, 30, 0, '+01:00'))

tz.local_time(2018, 2, 1, 7, 30, 0)
tz.local_time(2018, 7, 1, 8, 30, 0)

tz.local_time(2018, 2, 1, 7, 30, 0).utc
tz.local_time(2018, 7, 1, 8, 30, 0).utc

tz.local_to_utc(Time.utc(2018, 2, 1, 7, 30, 0))
tz.local_to_utc(Time.new(2018, 2, 1, 7, 30, 0, '+01:00'))

local_time = tz.to_local(Time.utc(2018, 2, 1, 12, 30, 0))
local_time.utc_offset
local_time.dst?
local_time.zone

local_time = tz.to_local(Time.utc(2018, 7, 1, 12, 30, 0))
local_time.utc.offset
local_time.dst?
local_time.zone

tz.to_local(Time.utc(2018, 2, 1, 12, 30, 0)).strftime('%Y-%m-%d %H:%M:%S %z %Z')
tz.to_local(Time.utc(2018, 7, 1, 12, 30, 0)).strftime('%Y-%m-%d %H:%M:%S %z %Z')

period = tz.period_for(Time.utc(2018, 7, 1, 12, 30, 0))
period.base_utc_offset
period.std_offset
period.current_utc_offset
period.abbreviation
period.dst?
period.local_starts_at.to_time
period.local_ends_at.to_time

transitions = tz.transitions_up_to(Time.utc(2018, 11, 1), Time.utc(2018, 11, 1))
transitions.map do |t|
  [t.local_end_at.to_time, t.offset.current_utc_offset, t.offset.abbreviation]
end

offsets = tz.offsets_up_to(Tim.utc(2018, 1, 1))
offsets.map {|o| [o.current_utc_offset, o.abbreviation] }

tz.to_local(Time.utc(2018, 7, 1, 12, 30, 0))
tz.to_local(DateTime.new(2018, 7, 1, 12, 30, 0))
tz.to_local(TZInfo::Timestamp.create(2018, 7, 1, 12, 30, 0, 0, :utc))

tz.local_time(2018, 2, 1, 7, 30, 0)
tz.local_datetime(2018, 2, 1, 7, 30, 0)
tz.local_timestamp(2018, 2, 1, 7, 30, 0)

tz.local_time(2018, 3, 11, 2, 30, 0, 0)
tz.local_time(2018, 11, 4, 1, 30, 0, 0)

tz.local_time(2018, 3, 11, 3, 30, 0, 0)

tz.local_time(2018, 11, 4, 1, 30, 0, 0, true)
tz.local_time(2018, 11, 4, 1, 30, 0, 0, false)
tz.local_time(2018, 11, 4, 1, 30, 0, 0){|p| p.first }
tz.local_time(2018, 11, 4, 1, 30, 0, 0)}{|p| p.last }

TZInfo::Timezone.default_dst = true
tz.local_time(2018, 11, 4, 1, 30, 0, 0)
TZInfo::Timezone.default_dst = false
tz.local_time(2018, 11, 4, 1, 30, 0, 0)

TZInfo::Country.all_codes

c = TZInfo::Country.get('US')
c.name

c.zone_identifiers

zi = c.zone_info.first
zi.identifier
zi.latitude.to_f.round(5)
zi.longitude.to_f.round(5)
zi.description

zi.timezone.to_local(Time.utc(2018, 2, 1, 12, 30, 0))

```

```
```


