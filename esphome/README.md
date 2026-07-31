# Example YAML

This is the yaml I use for my AC units. Make sure to go through all the options to see if it fits your device before installing it. 

Most of the configuration comes from examples at https://github.com/echavet/MitsubishiCN105ESPHome with some added bits and pieces...

### Dew Point Control

I added a simple dew point control that gets active the moment the AC is set to dry mode. It uses the dew point sensor and adds 10°C to move it into the valid area for the AC. So if you want to get to a dew point of 13°C set the AC to dry and 23°C

When switching modes it takes a few seconds for the temperature to update. No worries if it doesn't happen immediately. 
