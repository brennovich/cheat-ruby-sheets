## CPF Ruby Api
```
# Check if a CPF is valid
CPF.valid?(14356412214)
# => true

# Generate a random CPF number
CPF.generate
# => 46859286873

# Generate a formatted number
CPF.generate(true)
# => "468.592.868-73"

# Return formatted CPF
cpf = CPF.new(46859286873)
cpf.formatted
# => "468.592.868-73"

# Return stripped CPF
cpf.stripped
# => 46859286873

# Check if CPF is valid
cpf.valid?
# => true
```

## CNPJ Ruby Api
```
# Check if a CNPJ is valid
CNPJ.valid?(26273132000180)
# => true

# Generate a random CNPJ number
CNPJ.generate
# => 26273132000180

# Generate a formatted number
CNPJ.generate(true)
# => "26.273.132/0001-80"

# Return formatted CNPJ
cnpj = CNPJ.new(26273132000180)
cnpj.formatted
# => "26.273.132/0001-80"

# Return stripped CNPJ
cnpj.stripped
# => 26273132000180

# Check if CNPJ is valid
cnpj.valid?
# => true
```

## Command Line
```
# Check if CPF is valid
cpf --check 532.820.857-96

# Return formatted cpf
cpf --format 53282085796
# => 532.820.857-96

# Return stripped CPF
cpf --strip 532.820.857-96
# => 53282085796

# Generate formatted cpf
cpf --generate
# => 417.524.931-17

# Generate stripped cpf
cpf --generate --strip
# => 76001454809
```