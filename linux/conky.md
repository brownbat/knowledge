## System Monitoring with Conky on Ubuntu

Conky is a system monitor for X. It is configurable and scriptable and is able to monitor various system parameters including CPU, memory, disk usage, network activity, and basically any stat that could generate a command-line output. It allows users to display system information on their desktop for performance monitoring and other status checks.

### Installing Conky

To install Conky on Ubuntu:

```bash
sudo apt install conky-all
```

### Configuring Conky

Below is a sample Conky configuration for a system with dual GPUs that also shows available updates. Save this configuration in the `~/.conkyrc` file.

```lua
conky.config = {
    alignment = 'top_right',
    background = true,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = '#D3D3D3', -- Light gray
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'DejaVu Sans Mono:size=10',
    gap_x = 20,
    gap_y = 60,
    minimum_width = 300,
    minimum_height = 400,
    maximum_width = 300,
    net_avg_samples = 2,
    double_buffer = true,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    own_window_transparent = false,
    own_window_colour = '#2E2E2E', -- Dark gray background
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false,
};

conky.text = [[
${color #FFB6C1}${font DejaVu Sans Mono:bold:size=10}CPU and Case${font}${color}
${hr 2}
${color #ADD8E6}Usage: ${goto 170} ${cpu cpu0}% 
${cpubar cpu0 10}${color}
${color #ADD8E6}Temp: ${goto 170}${execi 10 sensors | grep 'Tctl' | awk '{print $2}'}${color}
${color #ADD8E6}CPU Fan: ${goto 170}${execi 10 sensors | grep 'fan2' | awk '{print $2}'} RPM${color}
${color #ADD8E6}Case fans (CHA_5): ${goto 170}${execi 10 sensors | grep 'fan6' | awk '{print $2}'} RPM${color}

${color #FFB6C1}${font DejaVu Sans Mono:bold:size=10}GPUs (0 and 1)${font}${color}
${hr 2}
${color #ADD8E6}GPU Usage: ${goto 170}${color #87CEFA}${execi 10 nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits -i 0}% ${color #00FF7F}/ ${execi 10 nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits -i 1}%${color}
${color #87CEFA}${execibar 10 nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits -i 0}${color}
${color #00FF7F}${voffset -8}${execibar 10 nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits -i 1}${color}
${color #ADD8E6}GPU Memory Usage: ${goto 170}${color #87CEFA}${execi 10 nvidia-smi --query-gpu=utilization.memory --format=csv,noheader,nounits -i 0}% ${color #00FF7F}/ ${execi 10 nvidia-smi --query-gpu=utilization.memory --format=csv,noheader,nounits -i 1}%${color}
${color #ADD8E6}Power Draw: ${goto 170}${color #87CEFA}${execi 10 nvidia-smi --query-gpu=power.draw --format=csv,noheader,nounits -i 0}W ${color #00FF7F}/ ${execi 10 nvidia-smi --query-gpu=power.draw --format=csv,noheader,nounits -i 1}W${color}
${color #ADD8E6}Core Temps: ${goto 170}${color #87CEFA}${execi 10 nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader,nounits -i 0}°C ${color #00FF7F}/ ${execi 10 nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader,nounits -i 1}°C${color}
${color #ADD8E6}GPU Fans: ${goto 170}${color #87CEFA}${execi 10 nvidia-smi --query-gpu=fan.speed --format=csv,noheader,nounits -i 0}% ${color #00FF7F}/ ${execi 10 nvidia-smi --query-gpu=fan.speed --format=csv,noheader,nounits -i 1}%${color}

${color #FFB6C1}${font DejaVu Sans Mono:bold:size=10}Memory and Storage${font}${color}
${hr 2}
${color #ADD8E6}RAM Usage: ${goto 170}$mem/$memmax - $memperc% 
${membar 10}${color}
${color #ADD8E6}Swap Usage: ${goto 170}$swap/$swapmax - $swapperc% 
${swapbar 10}${color}
${color #ADD8E6}Buffers: ${goto 170}$buffers${color}
${color #ADD8E6}Cached: ${goto 170}$cached${color}
${color #ADD8E6}Storage: ${goto 170}${fs_used /}/${fs_size /} 
${fs_bar 10 /}${color}
${color #ADD8E6}Read/Write: ${goto 170}${diskio_read}/${diskio_write}${color}

${color #FFB6C1}${font DejaVu Sans Mono:bold:size=10}Network${font}${color}
${hr 2}
${color #ADD8E6}Down: ${downspeedf wlp9s0} KiB/s${color}
${color #90EE90}${downspeedgraph wlp9s0 25,240 ADD8E6 ADD8E6}${color}
${color #ADD8E6}Up: ${upspeedf wlp9s0} KiB/s${color}
${color #90EE90}${upspeedgraph wlp9s0 25,240 ADD8E6 ADD8E6}${color}

${color #FFB6C1}${font DejaVu Sans Mono:bold:size=10}Top Processes${font}${color}
${hr 2}
${color #ADD8E6}${goto 35}PID    CPU%    MEM% Command${color}
${color #90EE90}${top pid 1}  ${top cpu 1}  ${top mem 1}${color} ${top name 1}
${color #ADD8E6}${top pid 2}  ${top cpu 2}  ${top mem 2}${color} ${top name 2}
${color #90EE90}${top pid 3}  ${top cpu 3}  ${top mem 3}${color} ${top name 3}
${color #ADD8E6}${top pid 4}  ${top cpu 4}  ${top mem 4}${color} ${top name 4}
${color #90EE90}${top pid 5}  ${top cpu 5}  ${top mem 5}${color} ${top name 5}

${color #FFB6C1}${font DejaVu Sans Mono:bold:size=10}Updates${font}${color}
${hr 2}
${color #ADD8E6}Updates Available: ${execi 3600 apt list --upgradeable 2>/dev/null | grep -c upgradable}${color}
]];
```
