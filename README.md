# ReportHub

ReportHub is an automated email reporting system that leverages MQTT messaging to generate and send business reports on demand.

## Features

- **MQTT-Based Messaging**: Receives reporting requests via MQTT topics
- **Automated Email Delivery**: Generates and sends formatted email reports
- **Web Automation**: Uses Selenium WebDriver for dynamic report generation
- **Notification System**: Built-in notification and action response handling
- **Configuration Management**: Flexible email report configuration
- **Docker Support**: Fully containerized for easy deployment

## Technology Stack

- **Runtime**: Node.js with TypeScript
- **Messaging**: MQTT v5
- **Email Automation**: Selenium WebDriver
- **Web Framework**: Express.js
- **Utilities**: RxJS, dayjs

## Prerequisites

- Node.js 18+
- Docker & Docker Compose (for containerized deployment)
- MQTT Broker
- Environment variables configured (see Setup)

## Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ReportHub
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   Create a `.env.development.local` file:
   ```
   MQTT_ADDRESS=mqtt://your-broker-address
   MQTT_USERNAME=your-username
   MQTT_PASSWORD=your-password
   ```

4. **Build TypeScript**
   ```bash
   npm run build
   ```

## Usage

### Local Development

```bash
npm start
```

### Docker Deployment

Build the Docker image:
```bash
docker build -t sempararempresas:dev .
```

Run the container:
```bash
docker run --env-file .env.development.local sempararempresas:dev
```

### Debug Mode

Enable Node.js inspector for debugging:
```bash
node --inspect=0.0.0.0:9229 ./src/app.js
```

## MQTT Topics

ReportHub listens to the following MQTT topic:

- **`semparar/sendReportsToEmail`**: Trigger email report generation and delivery with email configuration

## Project Structure

```
src/
├── app.ts              # Main application entry point
├── mqtt.ts             # MQTT connection and messaging handler
├── models/             # Data models
│   ├── EmailReportsConfig.ts
│   ├── Message.ts
│   ├── Notification.ts
│   └── ...
└── reports/            # Report generation logic
    └── EmailReports.ts
```

## Models

### EmailReportsConfig
Configuration for email report generation including recipient, subject, and content settings.

### ResponseMessage
Generic message wrapper for MQTT communications.

### Notification & NotificationAction
Handles notification events and associated actions.

## Development

The project uses TypeScript for type safety and includes compilation to JavaScript for runtime execution.

Watch mode for development:
```bash
tsc --watch
```

## License

See LICENSE file for details.

## Support

For issues or questions, please refer to the project repository or contact the development team.
