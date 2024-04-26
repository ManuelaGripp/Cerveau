
Para a criação de componentes estamos utilizando:
- Tailwind
- CVA
- TwMerge
- Storybook

### Etapas

1. Criar pasta com o arquivo do componente dentro de svc --> presentation --> components.

```typescript
import { cva, type VariantProps } from 'class-variance-authority'
import { cn } from '@/infra/utils/cn'

const componentNameVariants = cva(
  'rounded-full font-bold px-4 py-1 ',
  {
    variants: {
      variant: {
        default: 'bg-gradient-to-b text-primary from-secondary to-secondary-600 ',
        secondary: ' bg-gradient-to-b from-primary to-primary-600  text-white ',
        error: 'bg-error bg-gradient-to-b from-error to-error-600 text-white',
      },
    },
    defaultVariants: {
      variant: 'default'
    }
  }
)

interface ComponentNameProps extends VariantProps<typeof componentNameVariants> {
  label: string,
  blink?: boolean,
  size?: string
}

const ComponentName = ({ variant, label, size='text-sm',blink = false }: ComponentNameeProps) => {
  return (
    <div className={cn([buttonVariants({ variant}),size,blink && 'animate-blink'])}>{label} {blink}</div>
  )
}

ComponentName.displayName = 'ComponentName'

export { ComponentName }
```

2. Criar o story do componente dentro de src --> stories.
```typescript

import { ComponentName } from 'path';
import type { Meta, StoryObj } from '@storybook/react';

// More on how to set up stories at: https://storybook.js.org/docs/writing-stories#default-export
const meta = {
  title: 'Component Name',
  component: ComponentName,
  parameters: {
    layout: 'centered',
  },
  tags: ['autodocs'],
} satisfies Meta<typeof ComponentName>

export default meta
type Story = StoryObj<typeof meta>

export const Primary: Story = {
  args: {
    label:'Adquira já!',
    size:'text-xs',
    blink:true,
  },
}

export const Secondary: Story = {
  args: {
    variant:'secondary',
    label:'Concluído',
    size:'text-sm'
  },
}

export const Error: Story = {
  args: {
    variant:'error',
    label:'Esgotado',
    size:'text-lg'
  },
}

```