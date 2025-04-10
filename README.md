# Phantom Knowledge Repository - Project Plan

## Project Overview
Building a comprehensive knowledge management system consisting of:

- **phantom-db**: PostgreSQL database for structured data storage  
- **phantom-db-editor**: Web interface for content management  
- **phantom-db-explorer**: Web interface for exploring and accessing content  
- **phantom-blog**: Integration with existing Hugo static site  
- **phantom-files**: Digital asset management system  

## Components & Technology Stack

### 1. phantom-db (Database)

**Technology**: PostgreSQL.
**Purpose**: Store structured information about people, books, films, etc.
**Status**: Partially implemented with tables and import scripts.

**Requirements**:
- Remote access for editing from different locations
- Efficient querying for content exploration
- Proper relationships between entities

---

### 2. phantom-db-editor (Content Management)

**Technology**:  
- **Backend**: FastAPI (Python)
- **Frontend**: React + Tailwind CSS

**Purpose**: Add, edit, and manage all content types

**Features**:
- Form-based editors for each content type (books, films, people)
- Validation against database schema
- Image upload and management
- Relationship management (linking authors to books, etc.)

**Key Libraries**:
- React Hook Form for validation
- React Query for data fetching
- Axios for API calls

---

### 3. phantom-db-explorer (Content Access)

**Technology**:  
- **Backend**: FastAPI (shares API with editor)
- **Frontend**: React + Tailwind CSS

**Purpose**: Search, filter, and browse content

**Features**:
- Advanced filtering (e.g., "French authors", "5-star movies")
- Sortable and filterable tables
- Grid/gallery views for visual content
- Export capabilities for integration with other systems

---

### 4. phantom-blog Integration

**Technology**: Hugo static site + API calls
**Current state**: Images stored in Git repository

**Integration Options**:
- API endpoints to query data for Hugo templates
- Image URL generation for blog posts
- Potentially JAMstack approach with React components in Hugo

---

### 5. phantom-files (Digital Assets)

#### **Books: Dedicated Document Server**  
**Technology**: Calibre Web (open-source ebook server)
**Features**:
- Organize PDFs and ebooks
- Metadata management
- Web-based reading
- API for integration with phantom-db

#### **Films: Already Managed in Plex**  
**Integration**: API links from phantom-db to Plex content

#### **Art/Images**  
**Options**:
- Host on a dedicated image server with thumbnail generation
- Use object storage (MinIO) for high-resolution originals
- Generate web-optimized versions for blog use

---

## Implementation Phases

### **Phase 1: Core Database & API**
- Complete database schema implementation
- Develop FastAPI backend with:
  - CRUD endpoints for all entities
  - Authentication/authorization
  - Validation logic
- API documentation and testing

### **Phase 2: Editor Interface**
- Develop React application scaffold
- Implement content type management screens
- Build form components with validation
- Create relationship management UI
- Implement image upload functionality

### **Phase 3: Explorer Interface**
- Build search and filter components
- Implement data visualization dashboards
- Create export functionality
- Add user preferences and saved searches

### **Phase 4: Integration & Document Management**
- Set up Calibre Web for ebook management
- Implement unified image management system
- Create API integration with Hugo blog
- Develop Plex integration for film content

---

## Technical Requirements

### **Infrastructure**
- **Database**: PostgreSQL on WSL2 with remote access
- **API Server**: FastAPI on same system
- **Web Application**: Static hosting or Node.js server
- **Document Server**: Calibre Web for ebooks
- **Media Server**: Existing Plex installation

### **Development Tools**
- **Backend**: Python 3.x, FastAPI, SQLAlchemy
- **Frontend**: React, Tailwind CSS, Vite
- **Documentation**: Swagger UI (via FastAPI)
- **Version Control**: Git

### **Deployment Considerations**
- Local development environment on WSL2
- Potential containerization with Docker for easier deployment
- SSL certificates for secure access
- Backup strategy for database and digital assets

### **Security & Access**
- Authentication for editor access
- Read-only public access for explorer interface
- Proper database credentials management
- Network security for remote access

---

## Future Expansion
- Mobile app for on-the-go cataloging
- AI-based recommendations
- OCR for digitizing physical documents
- Advanced analytics on collection